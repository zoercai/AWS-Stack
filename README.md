# AWS-Stack
AWS stack created with Cloudformation consisting of Lambda, Kinesis, API Gateway, and DynamoDB

## To See Things Working

In project root directory, run `mvn package`.

Upload the Cloudformation template to S3:

`aws s3 cp cloudformation.template s3://zoe-test-cloudformation/test-lambda-project.template`

Upload the packaged project jar to S3:

`aws s3 cp target/lambda-java-example-1.0-SNAPSHOT.jar s3://zoe-lambda-test/lambda-java-example-1.0-SNAPSHOT.jar`

To create a new stack:

`aws cloudformation create-stack --stack-name {your-stack-name} --template-url https://s3-ap-southeast-2.amazonaws.com/zoe-test-cloudformation/test-lambda-project.template`

Alternatively, update the existing stack:

`aws cloudformation update-stack --stack-name ZoeJavaLambdaStack3 --template-url https://s3-ap-southeast-2.amazonaws.com/zoe-test-cloudformation/test-lambda-project.template`

Then log into AWS console. Open API Gateway to test the GET method. Open Lambda to see the two handlers. ProcessKinesisEvents can be tested using "Configure new test" and selecting kinesis as the input.

## Other Things
* Role specified in cloudformation should have the correct policies attached with enough permissions
* Handlers should always implement the RequestHandler interface
