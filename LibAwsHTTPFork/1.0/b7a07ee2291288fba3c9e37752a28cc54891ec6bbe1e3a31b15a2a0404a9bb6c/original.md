```
aws_http_proxy_config_new_from_manager_options(allocator, options)
```

Create a persistent proxy configuration from http connection manager options

# Arguments

  * `allocator`: memory allocator to use
  * `options`: http connection manager options to source proxy configuration from

# Returns

### Prototype

```c
struct aws_http_proxy_config *aws_http_proxy_config_new_from_manager_options( struct aws_allocator *allocator, const struct aws_http_connection_manager_options *options);
```
