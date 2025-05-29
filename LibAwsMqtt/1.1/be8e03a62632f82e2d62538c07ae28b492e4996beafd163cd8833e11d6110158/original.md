```
aws_mqtt5_client_outbound_topic_alias_behavior_type
```

Outbound topic aliasing behavior is controlled by this type.

Topic alias behavior is described in https://docs.oasis-open.org/mqtt/mqtt/v5.0/os/mqtt-v5.0-os.html#_Toc3901113

If the server allows topic aliasing, this setting controls how topic aliases are used on PUBLISH packets sent from the client to the server.

If topic aliasing is not supported by the server, this setting has no effect and any attempts to directly manipulate the topic alias id in outbound publishes will be ignored.
