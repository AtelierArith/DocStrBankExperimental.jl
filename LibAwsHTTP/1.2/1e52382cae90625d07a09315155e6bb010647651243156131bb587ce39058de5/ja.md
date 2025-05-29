```
aws_http_message_get_response_status(response_message, out_status_code)
```

レスポンスメッセージのみのステータスコードを取得します。ステータスが設定されていない場合、AWS*ERROR*HTTP*DATA*NOT_AVAILABLEが発生します。

### プロトタイプ

```c
int aws_http_message_get_response_status(const struct aws_http_message *response_message, int *out_status_code);
```
