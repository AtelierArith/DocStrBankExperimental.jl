```
aws_http_proxy_strategy_create_negotiator(strategy, allocator)
```

プロキシ戦略から新しいプロキシネゴシエーターを作成します

# 引数

  * `allocator`: 使用するメモリアロケーター
  * `strategy`: 新しいネゴシエーターを作成するための戦略

# 戻り値

成功した場合は新しいプロキシネゴシエーター、そうでない場合はNULL

### プロトタイプ

```c
struct aws_http_proxy_negotiator *aws_http_proxy_strategy_create_negotiator( struct aws_http_proxy_strategy *strategy, struct aws_allocator *allocator);
```
