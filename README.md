Angular 11 JWT Authentication example
Flow for User Registration and User Login
For JWT – Token based Authentication with Web API, we’re gonna call 2 endpoints: - POST api/auth/signup for User Registration - POST api/auth/signin for User Login

You can take a look at following flow to have an overview of Requests and Responses that Angular 10 Client will make or receive.

angular-11-jwt-authentication-flow

Angular JWT App Diagram with Router and HttpInterceptor
angular-11-jwt-authentication-overview

For more detail, please visit:

Angular 11 JWT Authentication & Authorization with Web API
With Spring Boot back-end
Angular + Spring Boot: JWT Authentication & Authorization example
Run ng serve for a dev server. Navigate to http://localhost:4200/.

With Node.js Express back-end
Angular + Node.js Express: JWT Authentication & Authorization example
Open app/_helpers/auth.interceptor.js, modify the code to work with x-access-token like this:

...

// const TOKEN_HEADER_KEY = 'Authorization'; // for Spring Boot back-end
const TOKEN_HEADER_KEY = 'x-access-token';   // for Node.js Express back-end

@Injectable()
export class AuthInterceptor implements HttpInterceptor {
  ...

  intercept(req: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {
    ...
    if (token != null) {
      // for Spring Boot back-end
      // authReq = req.clone({ headers: req.headers.set(TOKEN_HEADER_KEY, 'Bearer ' + token) });

      // for Node.js Express back-end
      authReq = req.clone({ headers: req.headers.set(TOKEN_HEADER_KEY, token) });
    }
    return next.handle(authReq);
  }
}

...
Run ng serve --port 8081 for a dev server. Navigate to http://localhost:8081/.

More practice

Angular 11 CRUD Application example with Web API
Angular 11 Pagination example using ngx-pagination
Angular 11 File Upload example with progress bar

Fullstack with Node.js Express:

Angular 11 + Node.js Express + MySQL
Angular 11 + Node.js Express + PostgreSQL
Angular 11 + Node.js Express + MongoDB
Angular 11 + Node.js Express: JWT Authentication & Authorization example

Fullstack with Spring Boot:

Angular 11 + Spring Boot + MySQL
Angular 11 + Spring Boot + PostgreSQL
Angular 11 + Spring Boot + MongoDB
Angular 11 + Spring Boot: File upload example
Angular 11 + Spring Boot: JWT Authentication & Authorization example

Fullstack with Django:

Angular 11 + Django Rest Framework
Angular 11 + Django + MySQL
Angular 11 + Django + PostgreSQL

Serverless with Firebase:

Angular 11 Firebase CRUD Realtime DB | AngularFireDatabase
Angular 11 Firestore CRUD | AngularFireStore
Angular 11 Upload File to Firebase Storage example

Integration (run back-end & front-end on same server/port)

How to Integrate Angular with Node.js Restful Services
How to Integrate Angular with Spring Boot Rest API
