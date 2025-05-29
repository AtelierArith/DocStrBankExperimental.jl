```
aws_mqtt_client_connection_set_reconnect_timeout(connection, min_timeout, max_timeout)
```

Sets the minimum and maximum reconnect timeouts.

The time between reconnect attempts will start at min and multiply by 2 until max is reached.

# Arguments

  * `connection`:[in] The connection object
  * `min_timeout`:[in] The timeout to start with
  * `max_timeout`:[in] The highest allowable wait time between reconnect attempts

### Prototype

```c
int aws_mqtt_client_connection_set_reconnect_timeout( struct aws_mqtt_client_connection *connection, uint64_t min_timeout, uint64_t max_timeout);
```
