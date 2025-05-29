```
aws_mqtt_client_release(client)
```

Decrements the ref count on an mqtt client. If the ref count drops to zero, the client is cleaned up.

# Arguments

  * `client`:[in] The client to release a ref count on

### Prototype

```c
void aws_mqtt_client_release(struct aws_mqtt_client *client);
```
