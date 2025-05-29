```
aws_http_proxy_strategy_new_tunneling_adaptive(allocator, config)
```

Constructor for an adaptive tunneling proxy strategy. This strategy attempts a vanilla CONNECT and if that fails it may make followup CONNECT attempts using kerberos or ntlm tokens, based on configuration and proxy response properties.

# Arguments

  * `allocator`: memory allocator to use
  * `config`: configuration options for the strategy

# Returns

a new proxy strategy if successfully constructed, otherwise NULL

### Prototype

```c
struct aws_http_proxy_strategy *aws_http_proxy_strategy_new_tunneling_adaptive( struct aws_allocator *allocator, struct aws_http_proxy_strategy_tunneling_adaptive_options *config);
```
