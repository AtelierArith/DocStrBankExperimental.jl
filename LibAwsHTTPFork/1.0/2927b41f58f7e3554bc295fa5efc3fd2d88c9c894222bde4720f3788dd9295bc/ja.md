```
aws_http_proxy_strategy_new_tunneling_adaptive(allocator, config)
```

適応型トンネリングプロキシ戦略のコンストラクタ。この戦略は、バニラCONNECTを試み、失敗した場合は、構成およびプロキシ応答プロパティに基づいて、kerberosまたはntlmトークンを使用してフォローアップCONNECTを試みることがあります。

# 引数

  * `allocator`: 使用するメモリアロケータ
  * `config`: 戦略のための構成オプション

# 戻り値

正常に構築された場合は新しいプロキシ戦略、そうでない場合はNULL

### プロトタイプ

```c
struct aws_http_proxy_strategy *aws_http_proxy_strategy_new_tunneling_adaptive( struct aws_allocator *allocator, struct aws_http_proxy_strategy_tunneling_adaptive_options *config);
```
