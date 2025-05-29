```
aws_http_proxy_config_new_from_proxy_options(allocator, options)
```

Create a persistent proxy configuration from non-persistent proxy options. Legacy connection type of proxy options will be rejected.

# Arguments

  * `allocator`: memory allocator to use
  * `options`: http proxy options to source proxy configuration from

# Returns

### Prototype

```c
struct aws_http_proxy_config *aws_http_proxy_config_new_from_proxy_options( struct aws_allocator *allocator, const struct aws_http_proxy_options *options);
```
