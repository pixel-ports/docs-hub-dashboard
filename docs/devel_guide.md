# Developer's Guide

## Introduction to the development
<div align="justify">

For the development of the Dashboard & Notifications component of PIXEL it has been necessary to create two solutions:

  - *Client solution*. Main component of this module and accesible via web to show the results obtained in the platform. It has been developed in **Element UI (Open source framework based on Vue.JS)**. There is a complete guide of how to develop with this framework [here](https://element.eleme.io/#/en-US). Next picture depicts the more important features of this solution.
<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/Dashboard_features.PNG" alt="Dashboard features" align="center" />
</p>

  - *Server solution*. **REST API** created to interact from the client solution with the different entities needed in certain processes (Visualizations, Dashboard, Alerts, etc). It is a **CRUD API** from which the accesses to the No-SQL DB that is being used (**MongoDB**) are made. This API follows the **MVC pattern**. The element **View** would be the view of the client solution itself. Within the **API** there will be only **Model** and **Controller**. It has been developed in **Node.JS**.

</div>
<br/><br/>

## Folder structure (Client solution)
<div align="justify">

The folder structure is marked by the chosen framework (**Element UI**).

Next picture depicts the folders and a brief description of their functionality.
<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/Meaning_folderStructure.PNG" alt="Folder structure" align="center" />
</p>

</div>
<br/><br/>

## Add new views
<div align="justify">

In case to add a new view to the platform the developer has to create the view inside the views folder (see next figure), creating its container folder.

<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/Views_folder.PNG" alt="Views folder" align="center" />
</p>

Once the view has been created it's time to add the view to the file responsible to manage the routes in the platform (router/index.js).

In this file, in addition to the paths for the different menu entries, it is configured:

  - **Navigability** between views. Even if the views don't have a menu entry.
  - **Icons** of the views that have menu entry.
  - **Nesting** of views within the same menu entry.

Next figure depicts the configuration in the index.js for the Map menu entry.
<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/map_menuEntry.PNG" alt="Map menu entry" align="center" />
</p>

</div>
<br/><br/>

## Internationalization
<div align="justify">

Platform PIXEL has the i18n configurations necessary to give support for the following languages:

  - *English*.
  - *Spanish*.
  - *French*.
  - *Italian*.
  - *Greek*.

The solution includes a folder called lang where the files for each  the languages it supports are located. To identify these languages they are called according to their **ISO Language Codes**. 

<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/language_folder.PNG" alt="Language's folder" align="center" />
</p>

The entries in these files are structured in regions according to the functionality to which the tag to be translated belongs. The figure below depicts the entries within the region alerts for the english file (**en.js**, according to the nomenclature mentioned above).

<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/alerts_region.PNG" alt="Alert's region" align="center" />
</p>

If PIXEL wants to **support a new language**, the developer should go to the  index.js file (in the language folder) and generate the necessary files (according to the content of index.js file). Finally, it will be necessary to create a JavaScript file named with the ISO Code for the new language.

The **syntax of the tag** to be created it will be different depending on its location within the view:
  - *HTML Code*. Next figure illustrates the syntax of the label in this case. This is the title tag within the widget region.
<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/HTML_tag.PNG" alt="HTML Code" align="center" />
</p>

  - *JavaScript Code*. Syntax is different in this case (see next figure). It is necessary to use the **'$t' method** that injects the necessary code to translate the tags by going to the corresponding file and region to retrieve the text of the tag.

<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/JavaScript_tag.PNG" alt="JavaScript Code" align="center" />
</p>

</div>
<br/><br/>

## Notifications
<div align="justify">

PIXEL Dashboard & Notifications includes two options to show notifications or messages to the end-user (without the need to build a custom popup or modal dialog).

  - *Message*. Method used to **notify a message to the end-user**. For example, the result of a validation. There are several levels of notifications: **warning, error or successful**. Also it is possible to indicate the time interval during which the message will be visible. The syntax of this type of notification is depicted in the next figure.
<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/message.PNG" alt="Syntax for  a Message" align="center" />
</p>

  Previous figure is showing a popup notifying that the delete action has been successful. 
  
  Next picture illustrate the appearance of this type of message. In that case, the result of a validation. A warning message.
<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/message_Example.PNG" alt="Example of Message" align="center" />
</p>

  - *Notification*. Method used to show the **result of an action** (entity created, updated, etc). There are different levels of messages attending to the result or priority of the action: warning, successful, error. The syntax of this type of message is depicted in the next figure.
<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/notification.PNG" alt="Syntax for Notifications" align="center" />
</p>

  Previous figure is showing a popup notifying that the entity has been created successfully.

  Next picture illustrates the appearance of this type of notification. In that case, an entity has been updated successfully.
<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/notification_Example.PNG" alt="Example of Notification" align="center" />
</p>

</div>
<br/><br/>

## Access to APIs
<div align="justify">

Dashboard interacts with the APIs of other components (as well as with the API of the server solution). These requests are not made directly from the corresponding view where necessary.

There is a folder called API where there is a JavaScript file for each of the entities or functionalities accessed via API.

<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/API_folder.PNG" alt="API's folder" align="center" />
</p>

For example:

  - *otools.js*. This is the file where the **PIXEL Operational Tools API endpoints** will be located.
<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/Endpoints_OTools.PNG" alt="Endpoints from Operational Tools API" align="center" />
</p>

  - *dataextractor_IH.js*. This file centralises all the **IH dataextractor API endpoints**.
<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/Endpoints_IH.PNG" alt="Endpoints from Information Hub API" align="center" />
</p>

  - *PAS_IH.js*. It contains the necessary methods to complete the PAS (Port Activity Scenario) forms. This information is stored in the **PIXEL Information Hub** and in this case there is no specific API. Queries are performed directly using the **elasticsearch REST API**.
<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/Endpoints_elasticsearch.PNG" alt="Endpoints from Elasticsearch search REST API" align="center" />
</p>

  - *resource.js*. It contains the endpoints exposed by the CRUD API created in the server solution.
<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/Endpoints_resource_entity.PNG" alt="Endpoints for the resource's entity" align="center" />
</p>

Each of these files has in common the import that is made in the first line. This imports the request class that will be used for each set of endpoints.

This request class contains:

  - *Base url* used in the request for each endpoint.
  - *Timeout configuration*. Can be different for each API.
  - *Construction of the response object* for each request.

Next figure depicts an example of request class (for the Operational Tools endpoints in this case).
<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/request_OTools.PNG" alt="Example of request class for the Operational Tools" align="center" />
</p>

</div>
<br/><br/>

## Add a new entity to the server solution
<div align="justify">

The server solution has been developed following the **MVC pattern (Model-View-Controller)**. Therefore, this pattern will be followed in case to add a new entity that will interact with the Dashboard.

Next figure depicts the folder structure of the server solution.
<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/folder_structure.PNG" alt="Folder structure of the server solution" align="center" />
</p>

Among these folders, the following stand out:

  - *controllers*. There will be controllers for each entity. **API entry point**. It is where the redirection of the method exposed to the internal method of our API is done. It makes use of the service classes.
<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/controller_file.PNG" alt="Controller file" align="center" />
</p>

  - *services*. It performs the queries against the database for this purpose makes use of the models.
<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/service_file.PNG" alt="Service file" align="center" />
</p>

  - *models*. It is in these classes that the object to be used for our entity will be defined (**properties, relations with other entities, etc.**).
<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/model_file.PNG" alt="Model file" align="center" />
</p>

There is a configuration file (index.js) where the developer must add a few lines for each of the entities to be exposed. These lines are related to the controller of the entity. This is because the access point to the API is through the controller.

This file is formed by two blocks:

  - *First block*. Where the **import of the controller's entity** is done.
<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/import_indexJS.PNG" alt="Imports for the controller's entity" align="center" />
</p>

  - *Second block*. Where the **path of the entity** of that controller is indicated.
<p align="center">
<img src="https://github.com/pixel-ports/docs-hub-dashboard/raw/master/docs/img/route_indexJS.PNG" alt="Example of controller file" align="center" />
</p>

</div>
<br/><br/>

## Add new visualizations
<div align="justify">
   
The src/components folder contains the various components of the dashboard client solution.

Among them, the widget folder stands out. This is where the **different widgets / visualizations** used to represent the information within the **PIXEL Platform** are created (displays associated with the execution of a model).

Therefore, in case you want to add a new type of visualization, this is where it should be done.

Currently, this folder is structured in the following subfolders:
  - *amcharts*. Views created using this JavaScript library.
  - *echart*. Views created using this JavaScript library.
  - *custom*. Custom views without the specific use of any JavaScript library.
  - *mixins*. Folder where we have files that help us to represent the visualizations. In this case the file responsible for resizing them (*resize.js*).

</div>


 
