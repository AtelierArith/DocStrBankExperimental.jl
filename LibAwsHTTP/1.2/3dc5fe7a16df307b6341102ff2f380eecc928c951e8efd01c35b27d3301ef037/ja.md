```
aws_http_proxy_config_new_clone(allocator, proxy_config)
```

既存のプロキシ設定をクローンします。リファクタリングによりこれを削除することができます（使用される1箇所で古いユーザーデータと新しいユーザーデータの「移動」を行う）が、これはこのロジックが呼び出される場所のテストケースがより良くなるまで待つべきです（ntlm/kerberosチェーン）。

# 引数

  * `allocator`: 使用するメモリアロケータ
  * `proxy_config`: クローンするhttpプロキシ設定

# 戻り値

### プロトタイプ

```c
struct aws_http_proxy_config *aws_http_proxy_config_new_clone( struct aws_allocator *allocator, const struct aws_http_proxy_config *proxy_config);
```
