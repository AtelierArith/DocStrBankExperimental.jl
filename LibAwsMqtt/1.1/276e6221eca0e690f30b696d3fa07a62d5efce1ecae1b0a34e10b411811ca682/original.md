```
aws_mqtt_library_init(allocator)
```

Initializes internal datastructures used by aws-c-mqtt. Must be called before using any functionality in aws-c-mqtt.

### Prototype

```c
void aws_mqtt_library_init(struct aws_allocator *allocator);
```
