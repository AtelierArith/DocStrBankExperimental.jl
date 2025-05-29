```
aws_tls_handler_server_name(handler)
```

クライアントモードのみ。これは、SNIおよびホスト名検証に使用されたサーバー名です。

### プロトタイプ

```c
struct aws_byte_buf aws_tls_handler_server_name(struct aws_channel_handler *handler);
```
