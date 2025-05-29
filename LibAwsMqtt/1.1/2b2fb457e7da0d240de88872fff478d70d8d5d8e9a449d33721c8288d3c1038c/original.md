```
aws_mqtt5_client_stop(client, disconnect_options, completion_options)
```

Asynchronous notify to the mqtt5 client that you want it to transition to the stopped state. When the client reaches the stopped state, all session state is erased.

# Arguments

  * `client`: mqtt5 client to stop
  * `disconnect_options`: (optional) properties of a DISCONNECT packet to send as part of the shutdown process

# Returns

success/failure in the synchronous logic that kicks off the stop process

### Prototype

```c
int aws_mqtt5_client_stop( struct aws_mqtt5_client *client, const struct aws_mqtt5_packet_disconnect_view *disconnect_options, const struct aws_mqtt5_disconnect_completion_options *completion_options);
```
