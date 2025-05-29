```
aws_http_headers_get_all(headers, name)
```

この名前を持つすべての値を取得し、新しい aws*string に結合します。この aws*string の破棄はあなたの責任です。この名前を持つヘッダーが複数ある場合、それらの値はカンマ区切りで追加されます。この名前を持つヘッダーがない場合、NULL が返され、AWS*ERROR*HTTP*HEADER*NOT_FOUND が発生します。

### プロトタイプ

```c
struct aws_string *aws_http_headers_get_all(const struct aws_http_headers *headers, struct aws_byte_cursor name);
```
