```
aws_http_stream_acquire(stream)
```

ストリームの参照カウントを取得し、解放されるまでクリーンアップされないようにします。

### プロトタイプ

```c
struct aws_http_stream *aws_http_stream_acquire(struct aws_http_stream *stream);
```
