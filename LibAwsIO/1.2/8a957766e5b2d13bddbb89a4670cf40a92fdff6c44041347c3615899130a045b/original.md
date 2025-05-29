```
aws_retry_strategy_acquire_retry_token(retry_strategy, partition_id, on_acquired, user_data, timeout_ms)
```

Attempts to acquire a retry token for use with retries. On success, on_acquired will be invoked when a token is available, or an error will be returned if the timeout expires. partition_id identifies operations that should be grouped together. This allows for more sophisticated strategies such as AIMD and circuit breaker patterns. Pass NULL to use the global partition.

### Prototype

```c
int aws_retry_strategy_acquire_retry_token( struct aws_retry_strategy *retry_strategy, const struct aws_byte_cursor *partition_id, aws_retry_strategy_on_retry_token_acquired_fn *on_acquired, void *user_data, uint64_t timeout_ms);
```
