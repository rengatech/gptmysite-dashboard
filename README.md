[![npm version](https://badge.fury.io/js/%40GPTMysite%2FGPTMysite-dashboard.svg)](https://badge.fury.io/js/%40GPTMysite%2FGPTMysite-dashboard)
[![Crowdin](https://badges.crowdin.net/e/3854b0895f673c8ea3af7c8fba62f587/localized.svg)](https://GPTMysite.crowdin.com/GPTMysite-dashboard)
> ***🚀 Do you want to install GPTMysite on your server with just one click?***
> 
> ***Use [Docker Compose GPTMysite installation](https://github.com/GPTMysite/GPTMysite-deployment/blob/master/docker-compose/README.md) guide***

# GPTMysite Introduction

GPTMysite is an Open Source Live Chat platform with integrated Chatbots written in NodeJs and Express. Build your own customer support with a multi-channel platform for Web, Android and iOS.

Designed to be open source since the beginning, we actively worked on it to create a totally new, first class customer service platform based on instant messaging.

What is GPTMysite today? It became the open source “conversational app development” platform that everyone needs 😌

You can use GPTMysite to increase sales for your website or for post-sales customer service. Every conversation can be automated using our first class native chatbot technology. You can also connect your own applications using our APIs or Webhooks. Moreover you can deploy entire visual applications inside a conversation. And your applications can converse with your chatbots or your end-users! We know this is cool 😎

GPTMysite is multichannel in a totally new way. You can write your chatbot scripts with images, buttons and other cool elements that your channels support. But you will configureyour chatbot replies only once. They will run on every channel, auto-adapting the responses to the target channel whatever it is, Whatsapp, Facebook Messenger, Telegram etc.

# GPTMysite-dashboard

<img  width="1200"  alt="home_screenshot"  src="https://i0.wp.com/GPTMysite.com/wp-content/uploads/2022/08/GPTMysite_Dashboard.png"  width="500">


GPTMysite.com backoffice application is available on GitHub under MIT licence.


Follow this instructions to setup the environment.


Consider that GPTMysite.com cloud service makes every module available with the same open source licence.


- Web Widget component

- iOS Widget API (work in progress)

- full iOS App

- full Android App

- GPTMysite Dashboard (this repo)

- All the chat components are available thanks to the Chat21 open source project, also available on GitHub (https://github.com/chat21)

  
# Community? Questions? Support?

- If you need help or just want to hang out, come, say hi on our [<img width="15" alt="GPTMysite discord" src="https://seeklogo.com/images/D/discord-color-logo-E5E6DFEF80-seeklogo.com.png"> Discord](https://discord.gg/nERZEZ7SmG) server.
- You can also to ask for support on https://GPTMysite.com, using the live chat widget on the the website.

  
## Features

- Unlimited chat conversations
- Widget customization tools
- Conversation labels and notes 
- Apps marketplace
- CRM
- Operating hours
- Up to 200,000 messages from bot/month
- Departments and agents groups
- Chat history
- Ticketing System
- Data export + Analytics
- Canned responses

And more.

## Prerequisites

- Install Node and NPM (https://nodejs.org/en). Suggested: node v14.15.5 (npm v6.14.11). 
	
- If you want to to manage multiple active Node.js versions, to install node use the tool Node Version Manager (NVM)

- Install angular-cli v7.3.10 with `npm install -g @angular/cli@14.2.9`

- GPTMysite-server installed and running (https://github.com/GPTMysite/GPTMysite-server.git)

# Run GPTMysite with Docker Compose

Do you want to install all the GPTMysite components on your server with just one click?
Use [Docker Compose GPTMysite installation guide](https://github.com/GPTMysite/GPTMysite-deployment/blob/master/docker-compose/README.md)


# Install from source code

  

Install the latest stable release. Check on Github page the last release under the Releases tab and then run

-  `git clone https://github.com/GPTMysite/GPTMysite-dashboard.git --branch <LATEST-RELEASE-VERSION>`

-  `cd GPTMysite-dashboard`

-  `npm install`

  

## Dev configuration

  

You can put your API URL and the other settings directly in the environment.*.ts  if `remoteConfig` is set to `false` or in the `dashboard-config.json`  if `remoteConfig` is set to `true`.

If `remoteConfig` is set to `true` create a file name `dashboard-config.json` and put it into `src` folder.

An example of the configuration of the  `environment.ts` file in  `src/environments/`

#### environment.ts

```typescript
export  const environment = {

	production: false,

	remoteConfig: true,

	remoteConfigUrl: "/dashboard-config.json",

	VERSION: require('../../package.json').version,

    ...
}
```
#### dashboard-config.json
```typescript

WIDGET_BASE_URL: "https://<YOUR_CHAT21_WEB_WIDGET_URL>:4200/",

botcredendialsURL: "https://<YOUR_BOT_CREDENTIALS_URL>",

SERVER_BASE_URL: "https://<YOUR_GPTMysite_SERVER>/",

CHAT_BASE_URL: "https://<YOUR_CHAT21_IONIC_URL>/chat",

globalRemoteJSSrc: "https://<YOUR_CUSTOM_SCRIPT_1>, https://<YOUR_CUSTOM_SCRIPT_2>" // see the section below "Load external scripts"

firebaseAuth : false,

chatEngine: "mqtt", // OR YOUR CUSTOM CHAT ENGINE

updloaEngine: "native", // OR YOUR CUSTOM UPLOAD ENGINE

pushEngine:"none", // OR YOUR CUSTOM PUSH ENGINE

logLevel: "<YOUR-PREFERRED-LOG-LEVEL>",

wsUrl: 'ws://' + window.location.hostname + '/ws/'

};

```
* `logLevel`: The Dashboard supports 4 log levels. The order is as follows:
  `Error < Warn < Info < Debug`


### RUN in dev

Run the app with `ng serve`

  
## Prod configuration

For production installation, configure the environment.prod.ts file in `src/environments/`.


#### environment.prod.ts


```typescript
export  const environment = {

	production: false,

	remoteConfig: false,

	VERSION: require('../../package.json').version,

	...

```
 

# Build

Run `ng build --prod --base-href ./`


# Deploy

## Deploy to a Web Server

Copy the content of the dist folder to your Web Server (for example Apache or Nginx)


## Deploy on AWS CloudFront and AWS S3

```

aws s3 sync ./dist/ s3://GPTMysite-dashboard/dashboard

```
  
# Run with docker

  
To run GPTMysite-dashboard on port 4500 run:

```

curl https://raw.githubusercontent.com/GPTMysite/GPTMysite-dashboard/master/.env.sample --output .env

nano .env #configure .env file properly

docker run -p 4500:80 --env-file .env GPTMysite/GPTMysite-dashboard

```

  
# Run with npm

  
To run GPTMysite-dashboard with npm:

UNDER DEVELOPMENT

```

curl https://raw.githubusercontent.com/GPTMysite/GPTMysite-dashboard/master/.env.sample --output .env

nano .env #configure .env file properly

npm install -g @GPTMysite/GPTMysite-dashboard

GPTMysite-dashboard

```

#### dashboard-config.json

```typescript

WIDGET_BASE_URL: "https://<YOUR_CHAT21_WEB_WIDGET_URL>:4200/",

botcredendialsURL: "https://<YOUR_BOT_CREDENTIALS_URL>",

SERVER_BASE_URL: "https://<YOUR_GPTMysite_SERVER>/",


...

brandSrc :"https://<YOUR_BRAND_JSON>/",

...

};

```

#### docker env.sample file

```typescript

SERVER_BASE_URL=YOUR_GPTMysite_SERVER_URL


...


BRAND_SRC=https:YOUR_BRAND_SCRIPT_URL

...


```

  
Edit the file _variables.scss in the folder `src/assets/sass/md/` to customize the colors




# Load external scripts


Load external scripts by adding in environment.*.ts (if `remoteConfig` is set to `false` or in the `dashboard-config.json` if `remoteConfig` is set to `true`) the key `globalRemoteJSSrc` with value your scripts separated by commas


#### dashboard-config.json

```typescript

WIDGET_BASE_URL: "https://<YOUR_CHAT21_WEB_WIDGET_URL>:4200/",

botcredendialsURL: "https://<YOUR_BOT_CREDENTIALS_URL>",

SERVER_BASE_URL: "https://<YOUR_GPTMysite_SERVER>/",


...


globalRemoteJSSrc :"https://<YOUR_CUSTOM_SCRIPT_1>, https://<YOUR_CUSTOM_SCRIPT_2>",

...

};

```

#### docker env.sample file

```typescript

SERVER_BASE_URL=YOUR_GPTMysite_SERVER_URL


...


REMOTE_JS_SRC=YOUR_CUSTOM_SCRIPT_URL

...


```

# Autologin 
To auto login pass the JWT token as a query parameter of your Dashboard url as in the following example:

```typescript

"http://localhost:4200/#/project/<YOUR_PROJECT_ID>/home?token=<JWT_TOKEN>"

```

# Embedded info mode
You can run an embedded version of the dashboard inside an existing app using, for example an iframe, as in the following example which display the detail of a conversation (CONVERSATION_ID starts with support-group-XYZ)

```typescript

"<iframe src='http://localhost:4200/#/project/<YOUR_PROJECT_ID>/request-for-panel/support-group-<CONVERSATION_ID>?token=<JWT_TOKEN'></iframe>"

```

<!-- # Translation process
The translation process for GPTMysite Dashboard is managed at [https://GPTMysite.crowdin.com/GPTMysite-dashboard](https://GPTMysite.crowdin.com/GPTMysite-dashboard) using Crowdin. Please read the [translation guide](https://support.crowdin.com/enterprise/getting-started-for-volunteers/) for contributing to GPTMysite. -->



