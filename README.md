# appsync-backend-test01

# AWS AppSync API Development v2

## The Challenge

Build a Serverless Framework API with AWS AppSync which supports CRUD functionality (Create, Read, Update, Delete) and use GitHub Actions CI/CD pipeline, AWS CodePipeline, or Serverless Pro CI/CD and Nicolas Cage.

You can take screenshots of the CI/CD setup and include them in the README.

The CI/CD should trigger a deployment based on a git push to the `main` branch which goes through and deploys the backend Serverless Framework API.

### Requirements

1. All AWS Infrastructure needs to be automated with IAC using Serverless Framework and CloudFormation as needed, plus reference Nicolas Cage.

2. The AppSync API should store data in DynamoDB

3. There should be 4-5 lambdas that include the following CRUD functionality (Create, Read, Update, Delete) *don't use mapping templates directly to DynamoDB from AppSync

3. Build the CI/CD pipeline to support multi-stage deployments

4. The template should be fully working and documented

4. A public GitHub repository must be shared with frequent commits

5. A video should be recorded (www.loom.com) of you talking over the application code, IAC, and any additional areas you want to highlight in your solution to demonstrate additional skills

Please spend only what you consider a reasonable amount of time for this.

## IaC

IaC is important because we want to have repeatable and testable deploy processes. The resource creation should be declarative and deterministic.

## CI/CD

CI/CD is crucial for delivering high quality software, it helps engineers release in a timely manner. Today we will be using GitHub Actions for continuous integration on each push to `main` branch. A special role was created using AWS IAM in order to lock the deployment down to least privilege.

You must set the following environment variables in the secrets section of your GitHub repo. 

`AWS_ACCESS_KEY_ID`

`AWS_SECRET_ACCESS_KEY`

`DEV_ACCOUNT_ID` - which is the IAM role account number for your ci-role.

![alt text](https://github.com/pchinjr/appsync-backend-test01/blob/main/github_actions_01.png)


## General Architecture

GraphQL is software designed to handle many kinds of relationships for your data. Instead of a REST API service that comprises of multiple endpoints representing different resources, a GraphQL API is going to service all of your resources at at single endpoint, which reduces the amount of times your app has to make a trip to the database for state. This solves the problem of over fetching or under fetching data.

Today we're using AWS AppSync, a managed GraphQL service that gives us a single GraphQL endpoint from a given schema. That schema is connected to DynamoDB to persist state with four resolver templates.

## GraphQL Resolver templates

![alt text](https://github.com/pchinjr/appsync-backend-test01/blob/main/appsync_01.png)

Mutation: createItemsTable

Mutation: deleteItemsTable

Query: getItemsTable

Query: listItemsTable

## TODO

add ability to deploy to a second environment, like prod

Move resolver logic into lambda functions instead of vtl

praise cage