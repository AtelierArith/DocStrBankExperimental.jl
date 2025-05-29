```
aws_retry_strategy_acquire_retry_token(retry_strategy, partition_id, on_acquired, user_data, timeout_ms)
```

リトライに使用するリトライトークンを取得しようとします。成功した場合、トークンが利用可能になると on*acquired が呼び出され、タイムアウトが切れるとエラーが返されます。partition*id は一緒にグループ化すべき操作を識別します。これにより、AIMD やサーキットブレーカーパターンなど、より洗練された戦略が可能になります。グローバルパーティションを使用するには NULL を渡します。

### プロトタイプ

```c
int aws_retry_strategy_acquire_retry_token( struct aws_retry_strategy *retry_strategy, const struct aws_byte_cursor *partition_id, aws_retry_strategy_on_retry_token_acquired_fn *on_acquired, void *user_data, uint64_t timeout_ms);
```
