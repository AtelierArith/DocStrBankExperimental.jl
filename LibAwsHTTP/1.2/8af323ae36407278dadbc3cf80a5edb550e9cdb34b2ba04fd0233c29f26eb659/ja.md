```
aws_http_proxy_config_new_from_proxy_options(allocator, options)
```

永続的なプロキシ構成を非永続的なプロキシオプションから作成します。プロキシオプションのレガシー接続タイプは拒否されます。

# 引数

  * `allocator`: 使用するメモリアロケータ
  * `options`: プロキシ構成のソースとなるHTTPプロキシオプション

# 戻り値

### プロトタイプ

```c
struct aws_http_proxy_config *aws_http_proxy_config_new_from_proxy_options( struct aws_allocator *allocator, const struct aws_http_proxy_options *options);
```
