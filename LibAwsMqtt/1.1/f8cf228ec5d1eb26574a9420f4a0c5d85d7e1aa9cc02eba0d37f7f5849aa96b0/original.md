```
aws_mqtt5_client_subscribe(client, subscribe_options, completion_options)
```

Queues a Subscribe operation in an mqtt5 client

# Arguments

  * `client`: mqtt5 client to queue a Subscribe for
  * `subscribe_options`: configuration options for the Subscribe operation
  * `completion_options`: Completion callback configuration. Invoked when the corresponding SUBACK is received or a failure condition is reached. An error code implies complete failure of the subscribe, while a success code implies the user must still check all of the SUBACK's reason codes for per-subscription feedback.

# Returns

success/failure in the synchronous logic that kicks off the Subscribe operation

### Prototype

```c
int aws_mqtt5_client_subscribe( struct aws_mqtt5_client *client, const struct aws_mqtt5_packet_subscribe_view *subscribe_options, const struct aws_mqtt5_subscribe_completion_options *completion_options);
```
