```
aws_retry_strategy_new_no_retry(allocator, config)
```

This retry strategy is used to disable retries. Passed config can be null. Calling [`aws_retry_strategy_acquire_retry_token`](@ref) will raise error `AWS_IO_RETRY_PERMISSION_DENIED`. Calling any function apart from the [`aws_retry_strategy_acquire_retry_token`](@ref) and [`aws_retry_strategy_release`](@ref) will result in a fatal error.

### Prototype

```c
struct aws_retry_strategy *aws_retry_strategy_new_no_retry( struct aws_allocator *allocator, const struct aws_no_retry_options *config);
```
