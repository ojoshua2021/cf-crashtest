# cf-crashtest
# Cloud Foundry Crash Test #

## Description ##

A simple Cloud Foundry application written in Golang and using the Binary buildpack. The purpose of this application is to simulate crash events, which can be triggered via `GET` request parameters.

## Usage ##

### Environment Variables ###

The initial state of the application can be set using the following environment variables:

* `SHOULDPASS` - A boolean value that determines if the connection should be immediately closed at start, refusing all inbound TCP connections.
* `DESIREDRESPONSECODE` - An integer value between `100` and `599` which will be used as the HTTP reponse code on all requests

### Web Requests ###

So long as the application is configured to accept TCP connections, its state may be altered by passing the following parameters via a `GET` request:
* `HealthCheckShouldPass` - A boolean value that determines if the connection should be immediately closed at start, refusing all inbound TCP connections.
* `HealthCheckDesiredResponseCode` - An integer value between `100` and `599` which will be used as the HTTP reponse code on all requests

Toggling the boolean value for whether the health check should pass disables all inbound connections and cannot be undone without restarting the application.
