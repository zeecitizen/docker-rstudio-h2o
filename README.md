# docker-rstudio-h2o
Run H2O in RStudio using this docker image


Place docker file to a folder such as at /home/linux_user/mydockerbuild

cd into this folder mydockerbuild

Run this command in terminal:
docker build --rm=true -t $USER/rstudio .

This command above will utilize the Dockerfile to download and build a docker image. 

Good news! We've built a linux docker image to run the RStudio server. Now lets run it. 

Run this command in terminal:
sudo docker run -d -p 8787:8787 -t $USER/rstudio

If running the above command is successful, we can access RStudio here: 
http://localhost:8787/

Login to RStudio using username: guest and password: guest

Now inside the browser GUI of RStudio write these commands:

install.packages("h2o", repos=(c("http://s3.amazonaws.com/h2o-release/h2o/master/1497/R", getOption("repos"))))
library(h2o)
localH2O = h2o.init(nthreads = -1)

The init command runs in such a way to utilize all cores of CPU for H2O. 

Finally in RStudio run this command: 

demo(h2o.gbm)

Thank you. 
