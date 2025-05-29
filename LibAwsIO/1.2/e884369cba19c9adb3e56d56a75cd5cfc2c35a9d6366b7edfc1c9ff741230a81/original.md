```
aws_retry_strategy_new_exponential_backoff(allocator, config)
```

Creates a retry strategy using exponential backoff. This strategy does not perform any bookkeeping on error types and success. There is no circuit breaker functionality in here. See the comments above for [`aws_exponential_backoff_retry_options`](@ref).

### Prototype

```c
struct aws_retry_strategy *aws_retry_strategy_new_exponential_backoff( struct aws_allocator *allocator, const struct aws_exponential_backoff_retry_options *config);
```
