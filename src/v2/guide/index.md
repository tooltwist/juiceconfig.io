---
title: Documentation
type: guide
order: 2
---

## Introduction
### What is Juice?
Juice is a config tool for AWS that assists programmers and non-programmers alike by creating a simple and intuitive process that ensures projects are managed effectively at each stage of product development and deployed correctly every time. This system promotes security, transparency and consistency above all. 

### How does it work? 
Juice allows users to declare the core elements required to run their programs in various environments. Once set up, generating a config file for a project in a selected environmnent is as easy as creating a deployment record on the applications page, then selecting 'configure' and following the prompts. Juice will generate a config file based on the variables and dependencies values that have been provided by the user.

Individual users can create a free account and begin storing values immediately. Additionally, users can pay a monthly subscription fee to upgrade their account to include organisations with members and teams. Members of an organisation have restricted access to its deployables and environments based on the admin settings. Each deployable and environment can be either public or will have a team of users chosen by the admin. This is ideal for companies with numerous versions of projects running in various environments used by their teams that require strict separation and consistency. 

### Why is it useful? 
Deployment can become a nightmare if your workflow relies on individuals to maintain consistent and accurate config files. Most programmers develop their own procedures for deployment and storing sensitive information. Whilst companies may have recommended best practices, it’s easy for things to slip through the cracks due to human errors such as miscommunication, inexperience or just plain-old laziness. These mistakes are not only annoying but can also be damaging to client relationships and pose serious security risks. This is where Juice becomes a valuable asset in your future deployments.

Juice provides a simple, easy-to-use solution for configuring projects that prevents easily-made human errors. The procedures provided by Juice are safe guarded to prevent unauthorised personnel from making potentially damaging changes to existing infrastructure or project configs, whilst also ensuring that sensitive information cannot be stored or accidentally replicated. This also ensures that config files are consistent, thorough and values are recorded carefully and thoughtfully. 

#### Objectives
* To make development a simple and standalone process by removing the complications of production config considerations.
* To prevent storing config values and secure information in the source code and build scripts.
* To provide restricted access to secure information and the production system.
* To offer simplified, consistent, error-free Ops by:
  * Defining all required variables;
  * Removing the risk of accidentally copying parameters from one environment to another;
  * Generating reliable templates and scripts;
  * Fast recognition of missing config values.
* To ensure that the same source code is used throughout, despite having different locations for the config definitions.
* To use the same Docker image across all non-dev environments.
* To remove duplicate entries of config values (e.g. server starts on specific port, client uses that port as it’s endpoint).

### Is it secure?
Juice does not store or manage any sensitive information. It is the users responsibility to ensure that sensitive information is not saved on the Juice database. Juice simply stores the deployable variable names and will only request variable values during the configuration process. This sensitive data is then stored in AWS Secrets Manager or in your local storage, depending on your requirements. Juice simply provides a procedure for recording config values that ensures smooth project deployment every time, <i>users should never try to store sensitive information</i>. 

## Getting Started
### How to register
You can register for an account using LoginService, a ToolTwist authentication tool. Sign up via the Juice homepage, using your email address and create a username and password for login. A verification email will be sent to your email address where you can confirm your membership. Once verified you can login using the homepage at www.juiceconfig.io. 

To sign up as an organisation first you will be required to create a personal account. Once your personal account has been set up, you can add an organisation on the My Account page. You will be required to enter payment details, add the name and details of your organisation, and can add users during this process.

<i>‘I forgot my password, what can I do?’</i> - Simply select the ‘forgot password’ option and a password reset will be sent to your chosen email address. 

### Setting up your account
#### Understanding your intended use
Juice can be used by individuals or businesses and caters to a variety of different roles. The way that you set up your account will reflect your intended use. If you wish set up a personal account to create a stream-lined config process but do not need to include other users, simply register at the login page and begin adding information. 

As a business, you will need to set up a personal account then create an organisation via the My Account page. As an admin for the organisation you can then invite users manually and individually select their accessibility based on their role for each deployable and/or environment once the account has been set up. Organisations can have multiple admins if required.

#### Getting to know the layout
There will be a variety of familiar terms that you will see on the website. To avoid unneccesary confusion, make sure you understand what they require before entering in any data:

Glossary | Description
------------- | -------------
Deployables  | Deployables are programs that will be deployed and can be either existing projects or dependencies that are required for deployment (such as mySQL, ContentService or LoginService).
Project | A project is a program that is in the process of development by the user. Not all deployables will be projects. 
Deployments | Deployments are deployables that have been or will be configured with a selected environment. You can create and configure a deployment on the Applications page.
Dependencies | Dependencies are deployables that are required to run exisiting projects and other deployables. For example, a project might require LoginService and ContentService to run, therefore they would be the projects' dependencies. To declare a dependency relationship between 2 deployables, both must be added to the deployables records first. A dependency might also have its own dependencies, which would be declared on its own deployable page.
Environments | Users can define any type of environment; local, UAT, production, etc. However they should be mindful of which users have access when working in teams to ensure the process stays undiluted.
Groups | Coming soon...
Variables | Variables are the configurable values that are required for each project to be deployed (such as endpoints or database name). Variables should be created for every deployable and their dependencies, and each variable will be given values when configuring a project. 
Healthcheck | This feature is available for deployments that have provided a valid url on the applications page. Juice will 'ping' the url to check the status of the website and provide a symbol and message to give feedback about whether it is running as expected. 
Versions | Juice allows multiple versions of the same deployable to be added. Each version has a git hash and build number, and can be verified using a token generated in the /Deployables/Tokens tab. 
Tokens | Tokens can be generated and sent to other users to approve, approve and deploy, or decline specific versions. 

#### Adding data
The rest is intuitive and the process of adding information is up to you. However, generally we might suggest the following order:

<u>For a personal account: </u>
<b>1. Deployables </b>- Add a new deployable to the deployables page to get started. Deployables require an owner/admin, which by default will be the user adding the deployable; deployable name; description; type; and, also has the option of adding a product owner. Deployables can be made public, which means that any user with a Juice account will be able to access the deployable and can configure it within their own environments. Ensure that you create deployables for both your projects and their dependencies.

{% raw %}
<br>
<br>
<div style="max-width: 600px;">
  <img style="width: 100%;" src="../../gifs/deployable.gif">
</div>
{% endraw %}

<b>2. Dependencies </b>- You can declare the relationship between deployables by clicking on a deployable and selecting 'Add new dependency' in the dependencies tab. Dependencies must be added as a deployable before a relationship can be declared. 

{% raw %}
<br>
<br>
<div style="max-width: 600px;">
  <img style="width: 100%;" src="../../gifs/dependency.gif">
</div>
{% endraw %}

<b>3. Variables </b>- Once all deployables have been added, their required variable names will need to be declared so they can be successfully configured later on. 

{% raw %}
<br>
<br>
<div style="max-width: 600px;">
  <img style="width: 100%;" src="../../gifs/variable.gif">
</div>
{% endraw %}

<b>4. Environments </b>- Adding environments will be the simplest part of the process. Simply add the names and specifications of your environments. If you are adding an AWS environment, you will need to provide information about your account.

{% raw %}
<br>
<br>
<div style="max-width: 600px;">
  <img style="width: 100%;" src="../../gifs/environment.gif">
</div>
{% endraw %}

<b>5. Deployments </b>- Once both deployables and environments have been set up, you can create a deployment record on the Applications page. Simply select the deployable and environment, then choose a name to identify the deployment. You can create multiple records for the same environment and deployable if you provide a different application name for each record. 

{% raw %}
<br>
<br>
<div style="max-width: 600px;">
  <img style="width: 100%;" src="../../gifs/deployment.gif">
</div>
{% endraw %}

<b>6. Configure </b>- To configure, select 'configure' on the deployment record of your choice. Here you can edit the details of the deployment, generate a config file, download documentation, and find commands for provisioning and connnecting to AWS. If you are trying to configure a non-secure environment, you can also enter values for the variables you have defined. This is not possible for secure environments, values will need to be provided within the security of AWS or the environment selected. 

<u>As an organisation: </u>
1. Create personal account.
2. Create organisation.
3. We haven't gotten this far yet xx

4. Next add the names and roles for users who will need access to Juice. The users tab will only be viewable for the superuser or read/write users. This displays a list of all users with access to your Juice account, their accessibility which can be edited, and the projects and environments that they are involved in. 
5. Lastly, as a superuser you will need to manually add users to each project or environment, or create read/write access for other users so that they can add themselves and members of their team to projects and environments where applicable. However, it is important to limit users that have read/write access to minimise the chances of human error.

{% raw %}
<br>
<br>
<div style="max-width: 600px;">
  <img style="width: 100%;" src="../../images/diagram.png">
</div>
{% endraw %}

## Configuring a project
### Overview
To configure any project you will first need to select the project in the relevant environment tab, then select ‘configure’. This will bring you to a screen that displays the projects variable names and the dependencies’ variable names. You will need to fill in all fields, then click send. This will create a text file that can be reformatted for your specific purposes. The next steps will be determined based on your required environment.

(SCREEN SHOT OF ENVIRONMENT>DEPLOYABLE>CONFIGURE BUTTON)
(SCREEN SHOT OF CONFIG FORM) 

#### Using Juice-client CLI in a Docker container
Our objective with juice-client is to use the same Docker image in different environments, whilst still updating the config files as your project develops. This means the same image will be used on the developers desktop machine/laptop AND on AWS servers during continuous integration (CI), development testing, User Acceptance testing (UAT), staging and production environments. In this sense, the applications are protected against unwarranted changes during deployment from one environment on to the next.

#### Where are the configs stored?
Depending on the environment, the config will be stored in either a flat JSON format or on AWS Secrets Manager. Examples:

```
export JUICE_CONFIG='file:::/opt/Development/Projects/juice/juice-config/local-server/volumes/juice/config/config-for-juice.json'

export JUICE_CONFIG='secrets_manager:::ap-southeast-1:::PHILTEST'
```

*In the second example, the ap-southeast-1:::PHILTEST part is an identifier provided by AWS Secrets Manager. See the AWS Documentation for details.

### Desktop development and testing
For desktop development and test environments, a flat file will be created with the config, which will then be sent to the application in its designated environment. This will not be a secure environment.

{% raw %}
<br>
<br>
<div style="max-width: 600px;">
  <img style="width: 100%;" src="../../images/2. NodeJS development.png">
</div>
{% endraw %}

### Pre-production and production
For pre-production and production environments, the flat file generated in desktop development and test environments will be reformatted based on your environments specific requirements. This will then be sent to AWS Secrets Manager where you will be required to provide authorisation before storing the new config. This will be a secure environment. It is only at this stage that sensitive values should be stored in the config file.

{% raw %}
<br>
<br>
<div style="max-width: 600px;">
  <img style="width: 100%;" src="../../images/1. Overview.png">
</div>
{% endraw %}

##### juice-client as a library in a NodeJS application
NodeJS applications will be able to access AWS Secrets Manager directly, as seen in the diagram below. This means that you will not be required to reformat the config file and it can be sent directly from Juice-client to AWS Secrets Manager. 

{% raw %}
<br>
<br>
<div style="max-width: 600px;">
  <img style="width: 100%;" src="../../images/3. NodeJS production.png">
</div>
{% endraw %}

NodeJS programs will require the juice-client package to be installed in order to access config values. To install juice-client package from NPM, simply run the following in your terminal:

```
 # npm install @tooltwist/juice-client --save
```
In your program you will be required to define the following values: 
```
  const juice = require('juice-client')

  let value = juice.stringValue(name, defaultValue/*optional*/)
  let value = juice.intValue(name, defaultValue/*optional*/)
```

The value returned will be determined by:
1. If the value is defined in the config it will be returned.
2. If a default value is specified, it will be returned.
3. If the default value is juice.OPTIONAL, then the default value for the type will be returned (an empty string, or -1 for numeric values).
4. If the default value provided is juice.MANDATORY, an exception is thrown. Typically the program should immediately log the error and shut down.
5. If no default is specified, then juice.MANDATORY is assumed.

#### juice-client as a library in non-NodeJS application
As non-NodeJS application config requirements are more complex, AWS Secrets Manager will access juice-client outside of the application, which in turn will use a flat file to configure and send to the application. 

{% raw %}
<br>
<br>
<div style="max-width: 600px;">
  <img style="width: 100%;" src="../../images/4. Java production.png">
</div>
{% endraw %}

Libraries for languages such as Java and GoLang are currently in progress. For now, we recommend using juice-client as a CLI. Check out the instructions in the next section.


### Using the CLI
##### juice-client as a CLI
{% raw %}
<br>
<br>
<div style="max-width: 600px;">
  <img style="width: 100%;" src="../../images/juice-client-cli-in-docker-container.png">
</div>
{% endraw %}

Docker images are created using a Dockerfile and using the “docker build” command. See the Docker documentation for more details. 

We’ll update the config files at the time the docker container starts, just before the application starts. For this to happen several things need to be set up:

1. Once juice-client is installed, we build the application’s Docker image. The Dockerfile will also need NodeJS installed prior to running these commands:

```
# Install juice-client
RUN mkdir /juice-client
WORKDIR /juice-client
RUN echo {} > package.json
RUN npm install --color false @tooltwist/juice-client --save

COPY config-template /juice-client-config-template

CMD ["bash", "some-script.sh"]
```

2. The script used to start the application should use juice-client to create the config files from template config files. For example:

```
CMD=/juice-client/node_modules/\@tooltwist/juice-client/lib/juice-client
node ${CMD} install /juice-client-config-template/template-config-file1.config /somewhere/config/real-config-file1.config
[check exit status (see example below)]
node ${CMD} install /juice-client-config-template/template-config-file2.xml /somewhere/config/real-config-file2.xml
[check exit status]
node ${CMD} install /juice-client-config-template/template-config-file3.json /somewhere/config/real-config-file3.json
[check exit status]
...
[start the application]
```

Binary files are copied without changes. ASCII and Unicode files are handled. An entire directory can be copied recursively.

```
CMD=/juice-client/node_modules/\@tooltwist/juice-client/lib/juice-client
node ${CMD} install /juice-client-template-config-directory /somewhere/config
if [ $? != 0 ] ; then
    echo FATAL ERROR WHILE INSTALLING CONFIG FILES.
    echo SERVER WILL SHUT DOWN
    sleep 60
    exit 1
fi
...
[start the application]
```

This command returns with zero if the install worked correctly and all config variables are assumed to be mandatory.

If any of the config files refer to a config value that has not been defined, the script should display an error message, pause for a short while, then shut down. The Docker container will be restarted by AWS ECS, and the sleep prevents it from cycling too fast through the recycles. The intention is that the admin will see the error and update AWS Secrets Manager with the missing config values.

3. AWS ECS requires to be told to start the Docker image with - 
a) Environment variable JUICE_CONFIG pointing to the appropriate AWS Secrets Manager secret.
b) ECS can assign a permissions ‘role’ to a running Docker container. This role grants the entity with the role (i.e. our Docker container) access to resources. The administrator should assign a role to our Docker container that has access to the specified AWS Secrets Manager secret.

And that’s it. Super simple, super intuitive.
Good luck and happy coding!