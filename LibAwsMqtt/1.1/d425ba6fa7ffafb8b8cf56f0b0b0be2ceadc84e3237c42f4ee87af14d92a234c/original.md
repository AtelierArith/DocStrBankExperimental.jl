```
aws_mqtt_client_acquire(client)
```

Increments the ref count to an mqtt client, allowing the caller to take a reference to it

# Arguments

  * `client`:[in] The client to increment the ref count on

# Returns

the mqtt client

### Prototype

```c
struct aws_mqtt_client *aws_mqtt_client_acquire(struct aws_mqtt_client *client);
```
