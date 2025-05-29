```
aws_http_stream_get_id(stream)
```

ストリームに関連付けられたHTTP/2 IDを取得します。h1ストリームにもIDがあります（http/2と同じ割り当て手順を使用）ので、追跡が容易になります。クライアントストリームの場合、これは[`aws_http_stream_activate`](@ref)()への成功した呼び出しの後のみ非ゼロになります。

### プロトタイプ

```c
uint32_t aws_http_stream_get_id(const struct aws_http_stream *stream);
```
