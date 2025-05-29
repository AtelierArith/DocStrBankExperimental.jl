```
aws_mqtt_client_connection_new(client)
```

Spawns a new connection object.

# Arguments

  * `client`:[in] The client to spawn the connection from

# Returns

a new mqtt connection on success, NULL otherwise

### Prototype

```c
struct aws_mqtt_client_connection *aws_mqtt_client_connection_new(struct aws_mqtt_client *client);
```
