```
aws_http_connection_get_channel(connection)
```

HTTP接続をホストしているチャネルを返します。この関数を言語バインディングに公開しないでください。

### プロトタイプ

```c
struct aws_channel *aws_http_connection_get_channel(struct aws_http_connection *connection);
```
