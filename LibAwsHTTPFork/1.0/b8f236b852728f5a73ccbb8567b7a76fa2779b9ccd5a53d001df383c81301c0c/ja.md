```
aws_http_message_add_header_array(message, headers, num_headers)
```

ヘッダーの配列をヘッダー配列の末尾に追加します。メッセージは基になる文字列のコピーを作成します。

これは、ヘッダーをスタック配列として定義する方が簡単な場合に便利なヘルパー関数です。add_headerを繰り返し呼び出す代わりに使用します。

### プロトタイプ

```c
int aws_http_message_add_header_array( struct aws_http_message *message, const struct aws_http_header *headers, size_t num_headers);
```
