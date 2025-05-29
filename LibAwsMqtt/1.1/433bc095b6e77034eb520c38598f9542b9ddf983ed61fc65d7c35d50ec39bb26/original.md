```
aws_mqtt5_listener_new(allocator, config)
```

Creates a new MQTT5 listener object. For as long as the listener lives, incoming publishes and lifecycle events will be forwarded to the callbacks configured on the listener.

# Arguments

  * `allocator`: allocator to use
  * `config`: listener configuration

# Returns

a new [`aws_mqtt5_listener`](@ref) object

### Prototype

```c
struct aws_mqtt5_listener *aws_mqtt5_listener_new( struct aws_allocator *allocator, struct aws_mqtt5_listener_config *config);
```
