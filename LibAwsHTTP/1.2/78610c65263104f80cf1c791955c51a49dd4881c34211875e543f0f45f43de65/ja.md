```
aws_http_proxy_options_init_from_config(options, config)
```

永続的なHTTPプロキシ設定から非永続的なHTTPプロキシオプションを初期化します。

# 引数

  * `options`: 初期化するHTTPプロキシオプション
  * `config`: 初期化ソースとして使用するHTTPプロキシ設定

### プロトタイプ

```c
void aws_http_proxy_options_init_from_config( struct aws_http_proxy_options *options, const struct aws_http_proxy_config *config);
```
