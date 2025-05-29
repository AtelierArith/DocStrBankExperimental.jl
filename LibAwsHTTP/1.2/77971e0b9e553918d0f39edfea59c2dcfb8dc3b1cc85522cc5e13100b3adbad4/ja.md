```
aws_http_message_get_body_stream(message)
```

ボディストリームを取得します。ボディストリームが設定されていない場合はNULLを返します。

### プロトタイプ

```c
struct aws_input_stream *aws_http_message_get_body_stream(const struct aws_http_message *message);
```
