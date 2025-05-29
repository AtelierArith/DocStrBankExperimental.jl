```
aws_http_proxy_config_new_from_connection_options(allocator, options)
```

HTTP接続オプションから永続的なプロキシ設定を作成します

# 引数

  * `allocator`: 使用するメモリアロケータ
  * `options`: プロキシ設定のソースとなるHTTP接続オプション

# 戻り値

### プロトタイプ

```c
struct aws_http_proxy_config *aws_http_proxy_config_new_from_connection_options( struct aws_allocator *allocator, const struct aws_http_client_connection_options *options);
```
