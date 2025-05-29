```
aws_http_message_get_request_method(request_message, out_method)
```

リクエストメッセージのみのメソッドを取得します。

### プロトタイプ

```c
int aws_http_message_get_request_method( const struct aws_http_message *request_message, struct aws_byte_cursor *out_method);
```
