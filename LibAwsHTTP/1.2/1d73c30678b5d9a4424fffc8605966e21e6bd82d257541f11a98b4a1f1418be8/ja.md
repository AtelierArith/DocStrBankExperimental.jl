```
aws_http_proxy_config_new_tunneling_from_proxy_options(allocator, options)
```

非永続的なプロキシオプションから永続的なプロキシ構成を作成します。結果として得られるプロキシ構成は、トンネリング接続タイプを前提としています。

# 引数

  * `allocator`: 使用するメモリアロケータ
  * `options`: プロキシ構成をソースとするHTTPプロキシオプション

# 戻り値

### プロトタイプ

```c
struct aws_http_proxy_config *aws_http_proxy_config_new_tunneling_from_proxy_options( struct aws_allocator *allocator, const struct aws_http_proxy_options *options);
```
