```
aws_http_message_erase_header(message, index)
```

指定されたインデックスのヘッダーを削除します。このインデックス以降のヘッダーはすべて1つ前の位置にシフトされます。

有効なインデックスが提供されている場合、この関数は失敗することはありません。それ以外の場合、AWS*ERROR*INVALID_INDEXが発生します。

### プロトタイプ

```c
int aws_http_message_erase_header(struct aws_http_message *message, size_t index);
```
