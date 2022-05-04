# This project objective is to work with minimal setup of Angular and it's features/architecture.

## Configuring the project setup

### Install Angular CLI globally with NPM and push a new branch to this remote (you can name your branch whatever you like):
```
npm install -g @angular/cli
git clone https://github.com/victor-nunesm/angular-tour.git && cd angular-tour
ng new angular-tour --skip-git
git checkout -b NAME_OF_YOUR_BRANCH
git push -u origin NAME_OF_YOUR_BRANCH
```
OBS: Always use Angular Router when the CLI setup asks. SCSS is commonly the most used stylesheets due to it's versatility in using both CSS and SASS.
OBS2: The flag "--skip-git" skips the GIT initialization in an Angular project. It is necessary since the repository is already created. 

### Install json-server in a temporary folder:

1.  install json server with npm:
```
npm i --save json-server
```
2.  Inside your project root folder, create a new folder named "tmp"
3.  navigate to this "tmp" folder
4.  create a new file called db.json
5.  create a NPM script in "package.json" to start both project and json-server:
```
...
"start:" "ng serve --port=5656"
"start:db": "json-server --watch ./tmp/db.json"
...
```

### Create a new Module structure with a service and import HttpClient in your APP
1. Setup the module with CLI:
```
ng g m pages/MODULE_NAME
ng g c pages/MODULE_NAME
ng g s pages/MODULE_NAME/SERVICE_NAME
```
2. in your app.module.ts, add HttpClient to the imports array
3. in your service, import the HttpClient service to the service constructor
4. create a public method that uses HttpClient to request data from JSON-SERVER:
```
getData() {
  return this.http.get<any[]>('http://localhost:3000/FEATURE_NAME')
}
```
5. now, use this method in your component onInit, and assign this observable to a property in the component body (remmember to inject the service in component constructor)
6. use the async pipe to display the fetched data in template. use a basic HTML table to display the list of data
```
...
<td *ngFor="let data of data$ | async">
  {{ data.name }}
</td>
...
```
7. commit your code for review.
