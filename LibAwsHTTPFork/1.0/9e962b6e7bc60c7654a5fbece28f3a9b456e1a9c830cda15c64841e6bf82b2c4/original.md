```
aws_http_proxy_strategy_new_basic_auth(allocator, config)
```

A constructor for a proxy strategy that performs basic authentication by adding the appropriate header and header value to requests or CONNECT requests.

# Arguments

  * `allocator`: memory allocator to use
  * `config`: basic authentication configuration info

# Returns

a new proxy strategy if successfully constructed, otherwise NULL

### Prototype

```c
struct aws_http_proxy_strategy *aws_http_proxy_strategy_new_basic_auth( struct aws_allocator *allocator, struct aws_http_proxy_strategy_basic_auth_options *config);
```
