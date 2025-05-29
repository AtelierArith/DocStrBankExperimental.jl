```
aws_http_message_get_header(message, out_header, index)
```

指定されたインデックスのヘッダーを取得します。この関数は、有効なインデックスが提供されている場合、失敗することはありません。それ以外の場合、AWS*ERROR*INVALID_INDEXが発生します。

基になる文字列はメッセージ内に格納されています。

### プロトタイプ

```c
int aws_http_message_get_header( const struct aws_http_message *message, struct aws_http_header *out_header, size_t index);
```
