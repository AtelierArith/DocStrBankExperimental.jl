```
aws_http_stream_send_response(stream, response)
```

レスポンスを送信します（「リクエストハンドラー」ストリームからのみ呼び出し可能）。レスポンスオブジェクトは、ストリームの on_complete が呼び出されるまで少なくとも生存している必要があります。

### プロトタイプ

```c
int aws_http_stream_send_response(struct aws_http_stream *stream, struct aws_http_message *response);
```
