```
aws_http_proxy_strategy_new_basic_auth(allocator, config)
```

基本認証を行うプロキシ戦略のコンストラクタで、リクエストまたはCONNECTリクエストに適切なヘッダーとヘッダー値を追加します。

# 引数

  * `allocator`: 使用するメモリアロケータ
  * `config`: 基本認証の構成情報

# 戻り値

正常に構築された場合は新しいプロキシ戦略、そうでない場合はNULL

### プロトタイプ

```c
struct aws_http_proxy_strategy *aws_http_proxy_strategy_new_basic_auth( struct aws_allocator *allocator, struct aws_http_proxy_strategy_basic_auth_options *config);
```
