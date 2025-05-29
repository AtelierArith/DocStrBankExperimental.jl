```
aws_retry_strategy_new_no_retry(allocator, config)
```

このリトライ戦略は、リトライを無効にするために使用されます。渡された config は null である可能性があります。[`aws_retry_strategy_acquire_retry_token`](@ref) を呼び出すと、エラー `AWS_IO_RETRY_PERMISSION_DENIED` が発生します。[`aws_retry_strategy_acquire_retry_token`](@ref) と [`aws_retry_strategy_release`](@ref) 以外の関数を呼び出すと、致命的なエラーが発生します。

### プロトタイプ

```c
struct aws_retry_strategy *aws_retry_strategy_new_no_retry( struct aws_allocator *allocator, const struct aws_no_retry_options *config);
```
