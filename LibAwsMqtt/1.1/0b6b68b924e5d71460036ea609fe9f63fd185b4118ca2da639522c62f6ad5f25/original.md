```
aws_mqtt5_client_unsubscribe(client, unsubscribe_options, completion_options)
```

Queues an Unsubscribe operation in an mqtt5 client

# Arguments

  * `client`: mqtt5 client to queue an Unsubscribe for
  * `unsubscribe_options`: configuration options for the Unsubscribe operation
  * `completion_options`: Completion callback configuration. Invoked when the corresponding UNSUBACK is received or a failure condition is reached. An error code implies complete failure of the unsubscribe, while a success code implies the user must still check all of the UNSUBACK's reason codes for per-topic-filter feedback.

# Returns

success/failure in the synchronous logic that kicks off the Unsubscribe operation

### Prototype

```c
int aws_mqtt5_client_unsubscribe( struct aws_mqtt5_client *client, const struct aws_mqtt5_packet_unsubscribe_view *unsubscribe_options, const struct aws_mqtt5_unsubscribe_completion_options *completion_options);
```
