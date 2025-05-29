```
aws_retry_token_release(token)
```

トークンの参照カウントを解放します。これは、[`aws_retry_strategy_schedule_retry`](@ref)()を呼び出して失敗した後、または[`aws_retry_token_record_success`](@ref)()を呼び出した後に常に呼び出すべきです。

### プロトタイプ

```c
void aws_retry_token_release(struct aws_retry_token *token);
```
