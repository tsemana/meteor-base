meteor-base
===========

Cloning to a new app
--------------------

1. Remove this section from the README
2. Change .meteor/.id (delete it and let Meteor regenerate it)


-------------------


#### Environment variables

This project uses the pauldowman:dotenv package to set environment variables in development mode (only). Rename the `dotenv.example` file in the root directory to `.env`. Edit the entries with the configuration needed for the app.

Whenever your application loads, these variables will be available in `process.env`:

#### Client-side settings

pauldowman:dotenv can't set the METEOR_SETTINGS env variable (https://github.com/okgrow/meteor-dotenv/issues/2) so we still need a settings.json file to set public (i.e. client-side) settings. Copy `settings.example.json` to `settings.json`. 

#### Testing

This project uses tests written in [Jasmine](http://jasmine.github.io/2.0/introduction.html)
using the [Jasmine extension](https://github.com/Sanjo/meteor-jasmine)
for the [Velocity testing framework](https://github.com/meteor-velocity/velocity)

Velocity is still under heavy development, and there are still some awkward
issues to work out.

If your tests don't seem to run on the first startup, OR if they fail unexpectedly (or pass unexpectedly) stop the server, run `meteor reset`, and `killall node`

See dotenv.example for some ENV vars that you might want to set for debug output and to use PhantomJS for unit tests.

To use PhantomJS instead of Chrome for the unit tests add JASMINE_BROWSER=PhantomJS.

##### Packages deactivated for Testing

The following packages interfer with / prevent the operation of the testing framework.
They've been commented out in the `.meteor/packages` file temporarily

```
u2622:persistent-session
```

##### Running tests in the console

Tests can be run in the console by typing `meteor --test`
There is currently [an issue where running tests in this way leaves processes running
after the tests have run](https://github.com/meteor-velocity/velocity/issues/180).
