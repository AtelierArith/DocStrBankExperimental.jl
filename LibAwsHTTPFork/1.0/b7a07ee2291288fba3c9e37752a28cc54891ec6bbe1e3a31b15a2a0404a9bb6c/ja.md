```
aws_http_proxy_config_new_from_manager_options(allocator, options)
```

HTTP接続マネージャオプションから永続的なプロキシ設定を作成します

# 引数

  * `allocator`: 使用するメモリアロケータ
  * `options`: プロキシ設定のソースとなるHTTP接続マネージャオプション

# 戻り値

### プロトタイプ

```c
struct aws_http_proxy_config *aws_http_proxy_config_new_from_manager_options( struct aws_allocator *allocator, const struct aws_http_connection_manager_options *options);
```
