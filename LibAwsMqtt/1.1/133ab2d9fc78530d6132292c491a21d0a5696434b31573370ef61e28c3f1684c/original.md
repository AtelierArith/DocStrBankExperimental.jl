```
aws_mqtt5_client_get_stats(client, stats)
```

Queries the client's internal statistics for incomplete operations.

# Arguments

  * `client`: client to get statistics for
  * `stats`: set of incomplete operation statistics

### Prototype

```c
void aws_mqtt5_client_get_stats(struct aws_mqtt5_client *client, struct aws_mqtt5_client_operation_statistics *stats);
```
