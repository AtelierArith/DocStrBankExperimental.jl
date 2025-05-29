```
aws_mqtt_client_connection_release(connection)
```

Decrements the ref count on an mqtt connection. If the ref count drops to zero, the connection is cleaned up. Note: cannot call this with lock held, since it will start the destroy process and cause a dead lock.

# Arguments

  * `connection`:[in] The connection object

### Prototype

```c
void aws_mqtt_client_connection_release(struct aws_mqtt_client_connection *connection);
```
