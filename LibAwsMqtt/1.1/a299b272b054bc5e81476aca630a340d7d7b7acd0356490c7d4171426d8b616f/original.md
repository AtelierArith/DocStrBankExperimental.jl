```
aws_mqtt_client_connection_acquire(connection)
```

Increments the ref count to an mqtt client connection, allowing the caller to take a reference to it

# Arguments

  * `connection`:[in] The connection object

# Returns

the mqtt connection

### Prototype

```c
struct aws_mqtt_client_connection *aws_mqtt_client_connection_acquire(struct aws_mqtt_client_connection *connection);
```
