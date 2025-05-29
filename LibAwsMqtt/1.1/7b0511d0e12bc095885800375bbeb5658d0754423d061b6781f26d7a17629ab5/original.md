```
aws_mqtt5_client_operation_queue_behavior_type
```

Controls how disconnects affect the queued and in-progress operations submitted to the client. Also controls how operations are handled while the client is not connected. In particular, if the client is not connected, then any operation that would be failed on disconnect (according to these rules) will be rejected.
