```
aws_http_proxy_config_new_from_proxy_options_with_tls_info(allocator, proxy_options, is_tls_connection)
```

永続的なプロキシ構成を非永続的なプロキシオプションから作成します。

# 引数

  * `allocator`: 使用するメモリアロケータ
  * `options`: プロキシ構成のソースとなるhttpプロキシオプション
  * `is_tls_connection`: 接続タイプがレガシーの場合に接続タイプを決定するためのメイン接続のtls接続情報

# 戻り値

### プロトタイプ

```c
struct aws_http_proxy_config *aws_http_proxy_config_new_from_proxy_options_with_tls_info( struct aws_allocator *allocator, const struct aws_http_proxy_options *proxy_options, bool is_tls_connection);
```
