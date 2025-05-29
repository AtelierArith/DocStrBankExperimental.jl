```
aws_http_message_get_const_headers(message)
```

メッセージの定数 [`aws_http_headers`](@ref) を取得します。

### プロトタイプ

```c
const struct aws_http_headers *aws_http_message_get_const_headers(const struct aws_http_message *message);
```
