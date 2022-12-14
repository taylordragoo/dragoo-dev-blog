---
template: blog-post
title: "Football Manager-clone with Vue, IndexedDB, Electron: Project Setup"
slug: /sports-simulator-intro
date: 2022-12-14 08:56
description: Vue, Dexie, Electron, Persistence, Offline
---
I’ve decided to start a new section of my blog where I work on various projects and then blog about them. I have been working on a Sports Simulation game for a while now and I would like to share the things I have learned along the way.

If you want to write a sports simulation game but feel overwhelmed or unsure where to start, it can be helpful to break it down into its core components. A sports simulation game typically needs a database to store all the relevant data, such as teams, players, and game results. It also needs code to interact with the data and a user interface to view it. 

Rather than looking at the source code of an existing game, which may be complex and challenging to understand, it's better to start from scratch and build the game yourself. This tutorial will help you learn and understand the concepts better.

To create a new Vue.js project using the command line interface (CLI), you will need to have the Vue CLI installed on your system. You can install it globally using npm like this:

```
npm install -g @vue/cli
```

Once you have the Vue CLI installed, you can create a new project by running the following command:

```
vue create sports-simulation
```

This will create a new project in a directory called `sports-simulation` using the default settings. After the project has been created, next we need to Electron to our Vue project. To add Electron to a Vue.js project created with the Vue CLI, you will need to have Electron installed on your system. You can install Electron globally using npm like this:

```
npm install -g electron
```

Once you have Electron installed, navigate to your Vue.js project directory and run the following command:

```
vue add electron-builder
```

This will add Electron support to your project using the `electron-builder` package. It will also add a few scripts to your `package.json` file that you can use to build and run your Electron app.

To run your Electron app, use the following command:

```
npm run electron:serve
```

This will start the Electron app in development mode, where the app will automatically reload when you make changes to the code. Next, we want to add Vuex-ORM to our project. Vuex-ORM is an object-relational mapping(ORM) plugin for Vue.js that allows you to use an ORM to manage the state of your Vuex store. It provides a powerful query builder API and many other features that make working with data in your Vue app easier, especially if you are already using Vuex for state management. It provides a powerful and flexible way to work with data, making your Vue.js app more scalable and maintainable.

To install Vuex-ORM, you will need to have npm or yarn installed on your system. Once you have a package manager installed, you can use it to install Vuex-ORM like this:

```
npm install vuex-orm
```

After Vuex-ORM has been installed, you will need to import it into your Vue.js app and register it as a plugin. Here is an example of how to do this:

```
import Vue from 'vue';
import VuexORM from 'vuex-orm';

let store = new Vuex.Store({
    plugins: [VuexORM.install()]
})
```

Once you have registered Vuex-ORM as a plugin, we can start using it to manage your app's data. 

Next, we are going to install a package called Dexie. Dexie is another library for managing data in web applications. However, the difference is it provides an API for working with IndexedDB, a low-level database that is built into web browsers. IndexedDB allows you to store and retrieve data in a structured way, and Dexie makes it easier to work with this data by providing a higher-level API that is similar to a NoSQL database.

It also includes features such as lazy loading, data change events, and transaction support. It has a strong focus on performance and reliability, making it a good choice for applications that need to work with large amounts of data.

To install Dexie, run this command:

```
npm install dexie
```

After Dexie has been installed, you can import it into your JavaScript code and start using it to manage your app's data. Here is an example of how to do this:

```
import Dexie from 'dexie';

const db = new Dexie('myDatabase');

db.version(1).stores({
  todos: '++id, title, completed'
});

db.todos.put({
  title: 'Do something',
  completed: false
});
```

In this lesson, we set up our project and prepared several packages for use in future lessons. Next, we will go over how Vue, Vuex-ORM and Dexie all work together to save data for offline use similar to how you would for a game like Football Manager.