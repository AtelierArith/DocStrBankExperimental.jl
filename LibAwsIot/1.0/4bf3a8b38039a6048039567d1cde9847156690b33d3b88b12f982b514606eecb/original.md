```
aws_secure_tunnel_send_message(secure_tunnel, message_options)
```

Queues a message operation in a secure tunnel

# Arguments

  * `secure_tunnel`: secure tunnel to queue a message for
  * `message_options`: configuration options for the message operation

# Returns

success/failure in the synchronous logic that kicks off the message operation

### Prototype

```c
int aws_secure_tunnel_send_message( struct aws_secure_tunnel *secure_tunnel, const struct aws_secure_tunnel_message_view *message_options);
```
