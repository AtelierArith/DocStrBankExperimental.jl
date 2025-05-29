```
aws_http_stream_cancel(stream, error_code)
```

フライト中のストリームをキャンセルします。HTTP/1.1 ストリームの場合、これは接続を閉じることに相当します。HTTP/2 ストリームの場合、これはストリームに対して `AWS_HTTP2_ERR_CANCEL` でリセットを呼び出すことに相当します。

ストリームは、他の理由で既に完了している場合や、ストリームがアクティブでない場合を除き、提供されたエラーコードで完了します。この場合、この呼び出しは影響を与えません。

### プロトタイプ

```c
void aws_http_stream_cancel(struct aws_http_stream *stream, int error_code);
```
