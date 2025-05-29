```
aws_websocket_upgrade(allocator, stream, options)
```

受信したHTTP接続をウェブソケット接続にアップグレードします。この関数は、リクエストハンドラーのon*request*doneコールバックから呼び出す必要があります。完全に構築されたリクエストを期待し、ハンドシェイクレスポンスの送信を処理し、チャンネルにウェブソケットハンドラーをインストールします。

### プロトタイプ

```c
struct aws_websocket *aws_websocket_upgrade( struct aws_allocator *allocator, struct aws_http_stream *stream, const struct aws_websocket_server_upgrade_options *options);
```
