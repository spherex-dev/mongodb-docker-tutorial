# Introduction

This repository provides a simple tutorial on how to start your own MongoDB database with a volume and authentication with a docker compose file.
To run the mongo server, run the following command from a terminal while in this directory `docker compose up -d`, to stop the container run the command `docker compose down`.

## Resetting the database

If you wish to reset the database to it's original state and re-create the root user, a simple method to accomplish this woulbe to do delete the docker volume, change the username and password of the root user and restart the container using the docker compose command. The docker container is defined as `mongo_volume` in the docker-compose file and can be deleted with `docker volume rm mongo_volume`.

## Testing authentication

Once the database is running, MongoDB authentication can be tested using the following command: `docker exec -it mongodb-docker-tutorial-mongo-1 mongosh -u admin -p admin`. Adjust the username and admin as necessary if changes have been made to either variables. If you end up using this docker compose file and commit it somewhere, it is best to not commit the username and password as part of the docker-compose, but rather delete them from the file instead. To test that logins that are incorrect, change the command to `docker exec -it mongodb-docker-tutorial-mongo-1 mongosh -u admin -p wrong_password` or something appropriate to see that authentication fails with the incorrect password.
