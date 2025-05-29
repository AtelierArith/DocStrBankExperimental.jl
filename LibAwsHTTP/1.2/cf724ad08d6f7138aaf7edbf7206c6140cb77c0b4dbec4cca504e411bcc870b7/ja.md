```
aws_http_message_set_request_path(request_message, path)
```

リクエストメッセージのみのパスとクエリの値を設定します。リクエストは基になる文字列のコピーを作成します。

### プロトタイプ

```c
int aws_http_message_set_request_path(struct aws_http_message *request_message, struct aws_byte_cursor path);
```
