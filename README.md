# Coworking Space Service Extension
The Coworking Space Service is a set of APIs that enables users to request one-time tokens and administrators to authorize access to a coworking space. This service follows a microservice pattern and the APIs are split into distinct services that can be deployed and managed independently of one another.

### Dependencies
#### Local Environment
1. Python Environment
2. 2. PostgreSql Database
3. Docker CLI - build and run Docker images locally
4. `kubectl` - run commands against a Kubernetes cluster
   
#### Remote Resources
1. AWS CodeBuild - build Docker images remotely
2. AWS ECR - host Docker images
3. Kubernetes Environment with AWS EKS - run applications in k8s
4. AWS CloudWatch - monitor activity and logs in EKS
5. GitHub - pull and clone code

### Project Submission
Please find all screenshots required for project submission in the 'project submission' folder in this github repo - https://github.com/nyedun22/udacity-project-3


### Setup
1. Configure a Database
2. Test Database Connection by connecting to a kubernetes pod or remotely via port forwarding.
3. Run Seed Files
4. Set up Kubernetes port-forwarding - _kubectl port-forward svc/postgresql-service 5433:5432 &_



### Running the Analytics Application Locally
In the `analytics/` directory:

1. Install dependencies -   _pip install -r requirements.txt_ or via homebrew for Mac. 

2. Run the application in app.py - If we set the environment variables by prepending them, it would look like the following: DB_USERNAME=username_here DB_PASSWORD=password_here python app.py

3. Verifying The Application by running reports: `curl <BASE_URL>/api/reports/daily_usage` or 'user_visits'

### Deploy the analytics application
1. Dockerize the application
   
2. Set up continuous integration via codebuild
- set environment variables via codebuild and ensure these are reflected in the buildspec.yaml file

3. Deploy application on Kubernetes
- create deployment file <deploy.yaml> and ensure environment variables are reflected across the configmap and secret yaml files.
-  ensure ECR image url is also included within the deploy.yaml file.

4. Verify deployment
Run: kubectl get svc

### Updating the active enivronment variables
To make changes to YAML file deploy.yaml or if changes to the config or secret variables, edit the cofigmap or secrets yaml files and then run: kubectl delete pod coworking-6ff66c9566-ljggf

To check these environment varibles have been changed run: 
kubectl delete pod coworking-6ff66c9566-ljggf


