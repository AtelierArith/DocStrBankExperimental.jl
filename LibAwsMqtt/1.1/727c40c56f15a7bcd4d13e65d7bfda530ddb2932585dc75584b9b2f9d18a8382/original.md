```
aws_mqtt5_client_inbound_topic_alias_behavior_type
```

Inbound topic aliasing behavior is controlled by this type.

Topic alias behavior is described in https://docs.oasis-open.org/mqtt/mqtt/v5.0/os/mqtt-v5.0-os.html#_Toc3901113

This setting controls whether or not the client will send a positive topic alias maximum to the server in its CONNECT packets.

If topic aliasing is not supported by the server, this setting has no net effect.
