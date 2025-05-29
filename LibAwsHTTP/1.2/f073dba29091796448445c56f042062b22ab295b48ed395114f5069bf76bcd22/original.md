```
aws_http_proxy_strategy_create_negotiator(strategy, allocator)
```

Creates a new proxy negotiator from a proxy strategy

# Arguments

  * `allocator`: memory allocator to use
  * `strategy`: strategy to creation a new negotiator for

# Returns

a new proxy negotiator if successful, otherwise NULL

### Prototype

```c
struct aws_http_proxy_negotiator *aws_http_proxy_strategy_create_negotiator( struct aws_http_proxy_strategy *strategy, struct aws_allocator *allocator);
```
