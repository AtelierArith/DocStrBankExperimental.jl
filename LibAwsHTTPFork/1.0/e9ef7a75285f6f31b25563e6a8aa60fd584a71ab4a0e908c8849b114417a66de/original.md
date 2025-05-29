```
aws_http_proxy_config_new_from_connection_options(allocator, options)
```

Create a persistent proxy configuration from http connection options

# Arguments

  * `allocator`: memory allocator to use
  * `options`: http connection options to source proxy configuration from

# Returns

### Prototype

```c
struct aws_http_proxy_config *aws_http_proxy_config_new_from_connection_options( struct aws_allocator *allocator, const struct aws_http_client_connection_options *options);
```
