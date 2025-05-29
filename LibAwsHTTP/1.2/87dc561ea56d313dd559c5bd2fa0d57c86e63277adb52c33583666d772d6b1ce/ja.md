```
aws_http_message_set_response_status(response_message, status_code)
```

レスポンスメッセージのみのステータスコードを設定します。

### プロトタイプ

```c
int aws_http_message_set_response_status(struct aws_http_message *response_message, int status_code);
```
