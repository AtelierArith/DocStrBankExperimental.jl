```
aws_mqtt_client_get_payload_for_outstanding_publish_packet(connection, packet_id, allocator, result)
```

result buffer will be initialized and payload will be written into it

### Prototype

```c
int aws_mqtt_client_get_payload_for_outstanding_publish_packet( struct aws_mqtt_client_connection *connection, uint16_t packet_id, struct aws_allocator *allocator, struct aws_byte_buf *result);
```
