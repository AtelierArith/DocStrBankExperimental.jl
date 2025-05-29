```
aws_secure_tunnel_stream_start(secure_tunnel, message_options)
```

Queue a STREAM_START message in a secure tunnel

!!! note
    This function should only be used from source mode.


# Arguments

  * `secure_tunnel`: secure tunnel to queue a message for
  * `message_options`: configuration options for the message operation

# Returns

success/failure in the synchronous logic that kicks off the message operation

### Prototype

```c
int aws_secure_tunnel_stream_start( struct aws_secure_tunnel *secure_tunnel, const struct aws_secure_tunnel_message_view *message_options);
```
