```
aws_mqtt5_client_start(client)
```

Asynchronous notify to the mqtt5 client that you want it to attempt to connect to the configured endpoint. The client will attempt to stay connected using the properties of the reconnect-related parameters in the mqtt5 client configuration.

# Arguments

  * `client`: mqtt5 client to start

# Returns

success/failure in the synchronous logic that kicks off the start process

### Prototype

```c
int aws_mqtt5_client_start(struct aws_mqtt5_client *client);
```
