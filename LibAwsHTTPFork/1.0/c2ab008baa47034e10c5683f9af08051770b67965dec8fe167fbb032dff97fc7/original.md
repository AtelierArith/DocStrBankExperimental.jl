```
aws_http_proxy_config_new_from_proxy_options_with_tls_info(allocator, proxy_options, is_tls_connection)
```

Create a persistent proxy configuration from non-persistent proxy options.

# Arguments

  * `allocator`: memory allocator to use
  * `options`: http proxy options to source proxy configuration from
  * `is_tls_connection`: tls connection info of the main connection to determine connection_type when the connection_type is legacy.

# Returns

### Prototype

```c
struct aws_http_proxy_config *aws_http_proxy_config_new_from_proxy_options_with_tls_info( struct aws_allocator *allocator, const struct aws_http_proxy_options *proxy_options, bool is_tls_connection);
```
