```
aws_http_message_add_header(message, header)
```

配列の末尾にヘッダーを追加します。メッセージは基になる文字列のコピーを作成します。

### プロトタイプ

```c
int aws_http_message_add_header(struct aws_http_message *message, struct aws_http_header header);
```
