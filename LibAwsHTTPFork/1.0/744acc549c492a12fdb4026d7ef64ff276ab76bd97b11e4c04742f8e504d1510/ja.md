```
aws_http_headers_set(headers, name, value)
```

ヘッダー値を設定します。必要に応じてヘッダーが追加され、この名前の既存の値は削除されます。基になる文字列はコピーされます。

### プロトタイプ

```c
int aws_http_headers_set(struct aws_http_headers *headers, struct aws_byte_cursor name, struct aws_byte_cursor value);
```
