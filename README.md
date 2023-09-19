[![CircleCI](https://dl.circleci.com/status-badge/img/gh/roshini777/Operationalise_ML_MicroService_API/tree/main.svg?style=svg)](https://dl.circleci.com/status-badge/redirect/gh/roshini777/Operationalise_ML_MicroService_API/tree/main)

## Project Overview

In this project, the task setup is to utilise skills you have acquired in this course to operationalize a Machine Learning Microservice API. 

A pre-trained, `sklearn` model was which has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on was given. Data has been initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). This project will operationalize a Python flask app—in a provided file, `app.py`—that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

### Project Tasks

I have worked to operationalize this machine learning microservice using [kubernetes](https://kubernetes.io/), which is an open-source system for automating the management of containerized applications. Below tasks have been accomplished, 

* Poject code has been tested using linting
* Dockerfile to containerize this application has been completed
* Deployed containerized application using Docker and made a prediction
* Improved the log statements in the source code for this application
* Configured Kubernetes and created a Kubernetes cluster
* Deployed a container using Kubernetes and made a prediction
* Uploaded a complete Github repo with CircleCI to indicate that my code has been tested


---

## Setup the Environment

I have used an Ubuntu Linux EC2 instance to setup the development environment. I have installed python 3.7 to ensure the project dependencies work as expected. Installed Docker, Kubectl, minikube

* Create a virtualenv with Python 3.7 and activate it. Refer to this link for help on specifying the Python version in the virtualenv. 
```bash

python3 -m pip install --user virtualenv

# Use a command similar to this one:
python3 -m virtualenv --python=<path-to-Python3.7> .devops
source .devops/bin/activate
```
* Run `make install` to install the necessary dependencies
* Run `make lint` to verify/lint the dockerfile

### Running `app.py` and Docker steps

1. Standalone:  `python app.py` - This will setup the flask app
2. Run in Docker:  `./run_docker.sh` - This script will build the docker container for flask app, list the docker images and start the container
3. Make prediction: `./make_prediction.sh` - This script will make the prediction for the model data while the docker container is running
4. Upload docker image: `./upload_docker.sh` - This script will upload the container image built to the docker hub setup on your account


### Kubernetes Steps

1. Start Minikube:  `minikube start` - This will start the minikube
2. Run in Kubernetes:  `./run_kubernetes.sh` - This script will start the Kubernetes pod and create flask app container pulling image from docker
3. Make prediction: `./make_prediction.sh` - This script will make the prediction for the model data  while the Kubernetes cluster is up & running

### Output log files for review under output_txt_files

1. docker_out.txt :  Logs from Docker run are available on this text file
2. kuberenetes_out.txt : Logs from Kubernetes run are available on this text file

### Circle CI Setup

The project has a pipeline setup in circleci [here](https://app.circleci.com/pipelines/github/roshini777/Operationalise_ML_MicroService_API?filter=all) The config.yml file has the steps described to build it. It has passed the run and the badge has been added on first line of the README.md file. 


