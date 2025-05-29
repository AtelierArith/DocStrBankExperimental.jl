```
aws_retry_token_release(token)
```

Releases the reference count for token. This should always be invoked after either calling [`aws_retry_strategy_schedule_retry`](@ref)() and failing, or after calling [`aws_retry_token_record_success`](@ref)().

### Prototype

```c
void aws_retry_token_release(struct aws_retry_token *token);
```
