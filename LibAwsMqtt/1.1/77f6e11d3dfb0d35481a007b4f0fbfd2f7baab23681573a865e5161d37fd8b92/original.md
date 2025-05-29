```
aws_mqtt5_client_new(allocator, options)
```

Creates a new mqtt5 client using the supplied configuration

# Arguments

  * `allocator`: allocator to use with all memory operations related to this client's creation and operation
  * `options`: mqtt5 client configuration

# Returns

a new mqtt5 client or NULL

### Prototype

```c
struct aws_mqtt5_client *aws_mqtt5_client_new( struct aws_allocator *allocator, const struct aws_mqtt5_client_options *options);
```
