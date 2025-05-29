```
aws_http_message_set_request_method(request_message, method)
```

メソッドを設定します（リクエストメッセージのみ）。リクエストは基になる文字列のコピーを作成します。

### プロトタイプ

```c
int aws_http_message_set_request_method(struct aws_http_message *request_message, struct aws_byte_cursor method);
```
