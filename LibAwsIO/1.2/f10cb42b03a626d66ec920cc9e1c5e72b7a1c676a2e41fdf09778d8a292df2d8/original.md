```
aws_retry_strategy_schedule_retry(token, error_type, retry_ready, user_data)
```

Schedules a retry based on the backoff and token based strategies. retry_ready is invoked when the retry is either ready for execution or if it has been canceled due to application shutdown.

This function can return an error to reject the retry attempt if, for example, a circuit breaker has opened. If this occurs users should fail their calls back to their callers.

error_type is used for book keeping. See the comments above for [`aws_retry_error_type`](@ref).

### Prototype

```c
int aws_retry_strategy_schedule_retry( struct aws_retry_token *token, enum aws_retry_error_type error_type, aws_retry_strategy_on_retry_ready_fn *retry_ready, void *user_data);
```
