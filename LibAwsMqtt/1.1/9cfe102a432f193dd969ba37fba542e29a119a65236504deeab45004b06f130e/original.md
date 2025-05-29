```
aws_mqtt5_client_publish(client, publish_options, completion_options)
```

Queues a Publish operation in an mqtt5 client

# Arguments

  * `client`: mqtt5 client to queue a Publish for
  * `publish_options`: configuration options for the Publish operation
  * `completion_options`: completion callback configuration. Successful QoS 0 publishes invoke the callback when the data has been written to the socket. Successful QoS1+ publishes invoke the callback when the corresponding ack is received. Unsuccessful publishes invoke the callback at the point in time a failure condition is reached.

# Returns

success/failure in the synchronous logic that kicks off the publish operation

### Prototype

```c
int aws_mqtt5_client_publish( struct aws_mqtt5_client *client, const struct aws_mqtt5_packet_publish_view *publish_options, const struct aws_mqtt5_publish_completion_options *completion_options);
```
