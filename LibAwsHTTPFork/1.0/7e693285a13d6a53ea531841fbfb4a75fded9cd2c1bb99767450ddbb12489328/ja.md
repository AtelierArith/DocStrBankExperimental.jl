```
aws_http_message_set_body_stream(message, body_stream)
```

ボディストリームを設定します。ボディがないメッセージにはNULLが許容されます。注意: メッセージはボディストリームの所有権を持ちません。メッセージが完了するまでストリームは破棄されてはいけません。

### プロトタイプ

```c
void aws_http_message_set_body_stream(struct aws_http_message *message, struct aws_input_stream *body_stream);
```
