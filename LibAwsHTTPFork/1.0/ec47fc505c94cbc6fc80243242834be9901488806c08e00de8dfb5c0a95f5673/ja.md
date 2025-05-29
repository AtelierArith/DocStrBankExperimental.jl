```
aws_http_header_name_eq(name_a, name_b)
```

両方の名前が同等であるかどうかを返します。これは大文字と小文字を区別しない文字列比較です。

例の一致: "Content-Length" == "content-length" // 大文字または小文字は問題ありません

例の不一致: "Content-Length" != " Content-Length" // 先頭の空白は悪いです

### プロトタイプ

```c
bool aws_http_header_name_eq(struct aws_byte_cursor name_a, struct aws_byte_cursor name_b);
```
