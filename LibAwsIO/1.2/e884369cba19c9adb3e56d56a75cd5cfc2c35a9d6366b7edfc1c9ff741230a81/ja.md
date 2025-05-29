```
aws_retry_strategy_new_exponential_backoff(allocator, config)
```

指数バックオフを使用したリトライ戦略を作成します。この戦略は、エラータイプや成功に関する帳簿管理を行いません。ここにはサーキットブレーカー機能はありません。 [`aws_exponential_backoff_retry_options`](@ref)に関するコメントを参照してください。

### プロトタイプ

```c
struct aws_retry_strategy *aws_retry_strategy_new_exponential_backoff( struct aws_allocator *allocator, const struct aws_exponential_backoff_retry_options *config);
```
