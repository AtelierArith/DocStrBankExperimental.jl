```
aws_retry_token_record_success(token)
```

成功したリトライを記録します。これは、トークンバケットを開放するための将来の決定を行うために使用されます。AIMDブレーカーなどの戦略の一部はこれを無視しますが、成功した操作の後には常にこれを呼び出すべきです。そうしないと、システムは障害時に回復しません。

### プロトタイプ

```c
int aws_retry_token_record_success(struct aws_retry_token *token);
```
