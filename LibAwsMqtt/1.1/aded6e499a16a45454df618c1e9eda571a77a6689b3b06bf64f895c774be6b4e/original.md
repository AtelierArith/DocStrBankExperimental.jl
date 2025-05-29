```
aws_mqtt_client_connection_get_stats(connection, stats)
```

Queries the connection's internal statistics for incomplete/unacked operations.

# Arguments

  * `connection`: connection to get statistics for
  * `stats`: set of incomplete/unacked operation statistics

# Returns

AWS_OP_SUCCESS if getting the operation statistics were successful, AWS_OP_ERR otherwise

### Prototype

```c
int aws_mqtt_client_connection_get_stats( struct aws_mqtt_client_connection *connection, struct aws_mqtt_connection_operation_statistics *stats);
```
