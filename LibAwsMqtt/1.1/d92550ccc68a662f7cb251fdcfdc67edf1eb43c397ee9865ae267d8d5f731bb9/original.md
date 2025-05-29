```
aws_mqtt5_negotiated_settings_init(allocator, negotiated_settings, client_id)
```

Initializes the Client ID byte buf in negotiated settings

# Arguments

  * `allocator`: allocator to use for memory allocation
  * `negotiated_settings`: settings to apply client id to
  * `client_id`: client id to set

### Prototype

```c
int aws_mqtt5_negotiated_settings_init( struct aws_allocator *allocator, struct aws_mqtt5_negotiated_settings *negotiated_settings, const struct aws_byte_cursor *client_id);
```
