# angular-k6xtra

[Edit on StackBlitz ⚡️](https://stackblitz.com/edit/angular-k6xtra)

Let me preface by saying, I'm assuming you and everyone who will be reading this is already comfortably with Angular 1 (now referred to as AngularJS, as opposed to simply Angular for the newer versions). That being said, let's get into some of the additions and key differences in Angular 2+.

They added an angular cli.
You can start a new project by running ng new [app name]. You can serve your project by running ng serve learn more here: https://github.com/angular/angular-cli

Your angular code is written in ES6 Typescript and it compiles at runtime to Javascript in the browser.
To get a full grasp on this I recommend checking out some the resource list I have at the bottom of my answer.

Project Structure
In a basic structure, you will have a app/ts folder where you'll be doing most your work and a app/js You'll find in the app/js folder files with a .js.map extension. They "map" your ".ts" files to your browser for debugging as your browser cannot read native typescript.

Update: It's out of beta. The project structure changed a bit, in most cases and if you're using the angular cli, you'll be working in the src/app/ folder. In a starter project, you'll have the following.

app.component.css 
app.component.html
app.component.spec.ts
app.component.ts 
app.module.ts
index.ts
app.component.css: CSS file you should use specific to the component.html

app.component.html: A view (variable declared in the app.component.js)

app.component.spec.ts: used for testing app.component.ts

app.component.ts: Your code that binds to app.component.html

app.module.ts: This it what kicks off your app and where you define all plugins, components, services, etc. This is the equivalent of the app.js in Angular 1

index.ts used to define or export project files

Additional information:
Pro tip: you can run ng generate [option] [name] to generate new services, components, pipes, etc.

Also the tsconfig.json file is important as it defines TS compile rules for your project.

If you're thinking I have to learn a whole new language?... Uh... kinda, TypeScript is a superset of JavaScript. Don't be intimidated; it's there to make your development easier. I felt like I had a good grasp on it after just a few hours playing with it, and had it all down after 3 days.

You bind to your HTML similarly like how you would if in an Angular 1 directive. So variable like $scope and $rootScope have been deprecated.
This one you may have been implied. Angular 2 is still a MV* but you'll be using 'components' as a way to bind code to your templates, for instance, take the following

    import { Component } from '@angular/core';

    @Component({
         selector:'my-app',
         template: '<h1> Hello World! </h1>'
    })

    export class AppComponent {}
Here think of the import statement as your dependency injection in a v1 controller. You use import to import your packages, where the import {Component} says you'll be making a component you'd like to bind to your HTML.

Notice the @Component decorator you have a selector and template. Here think of the selector as your $scope that you use like you use v1 directives where the name of the selector is what you use to bind to your HTML like so

<my-app> </my-app>
Where <my-app> is the name of your custom tag you'll use that will act as a placeholder for what's declared in your template. i.e.) <h1> Hello World! </h1>. Whereas this would look like the following in v1:

HTML

<h1>{{hello}}</h1>
JS

$scope.hello = "Hello World!"
Also can you add something between these tags to generate a loading message, like this:

<my-app> Loading... </my-app> 
Then it will display "Loading..." as the loading message.

Note that what's declared in template is the path or the raw HTML you'll be using in your HTML in your selector tag.

A fuller implementation of Angular 1 would look more like this:

HTML

<h1 ng-controller="myCtrl">{{hello}}</h1>
In v1 this would look something like

JS

angular.module('controller', [])



.controller('myCtrl', function( $scope) {
    $scope.hello = "Hello World!"
})
This is what I really like about v2. I found directive was a steep learning curve for me in v1 and even when I had them figured out I often had the CSS render not how I intended. I find this is way simpler.

V2 allows for easier scalability of your app since you can break up your app up easier than you could in v1. I like this approach as you can have all your working parts in one file as opposed to having several in angular v1.

What about converting your project from v1 to v2?

From what I've heard from the development team if you'd like to update your v1 project to v2 you'll just be going through and deleting deprecated blobs and replace your $scopes with selectors. I found this video helpful. It's with some of the Ionic team that are working side by side with the angular team as v2 has a stronger focus on mobile https://youtu.be/OZg4M_nWuIk Hope this helps.

UPDATE: I updated by adding examples as official implementations of Angular 2 have surfaced.

UPDATE 2: This still seems to be a popular question so I just thought I'd some resource I found very helpful when I started working with angular 2.

Helpful Resources:
For more on ES6, I recommend checking out The New Boston's ECMAScript 6 / ES6 New Features Tutorials - YouTube Playlist

To write Typescript functions and see how they compile to Javascript check out the Typescript language Playground

To see a function by function breakdown of what the Angular 1 equivalence is in Angular 2 see the Angular.io - Cookbook -A1 A2 Quick Reference
