```
aws_http_client_connect(options)
```

非同期的にクライアント接続を確立します。操作が接続を作成したか失敗したときに on_setup コールバックが呼び出されます。

### プロトタイプ

```c
int aws_http_client_connect(const struct aws_http_client_connection_options *options);
```
