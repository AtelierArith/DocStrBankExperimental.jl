```
aws_mqtt5_client_acquire(client)
```

Acquires a reference to an mqtt5 client

# Arguments

  * `client`: client to acquire a reference to. May be NULL.

# Returns

what was passed in as the client (a client or NULL)

### Prototype

```c
struct aws_mqtt5_client *aws_mqtt5_client_acquire(struct aws_mqtt5_client *client);
```
