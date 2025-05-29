```
aws_mqtt_client_connection_new_from_mqtt5_client(client)
```

Creates a new MQTT311 connection object that uses an MQTT5 client under the hood

# Arguments

  * `client`:[in] The mqtt5 client to create the connection from

# Returns

a new mqtt (311) connection on success, NULL otherwise

### Prototype

```c
struct aws_mqtt_client_connection *aws_mqtt_client_connection_new_from_mqtt5_client(struct aws_mqtt5_client *client);
```
