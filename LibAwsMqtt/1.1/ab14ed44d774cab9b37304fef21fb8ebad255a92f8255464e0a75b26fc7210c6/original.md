```
aws_mqtt5_client_release(client)
```

Release a reference to an mqtt5 client. When the client ref count drops to zero, the client will automatically trigger a stop and once the stop completes, the client will delete itself.

# Arguments

  * `client`: client to release a reference to. May be NULL.

# Returns

NULL

### Prototype

```c
struct aws_mqtt5_client *aws_mqtt5_client_release(struct aws_mqtt5_client *client);
```
