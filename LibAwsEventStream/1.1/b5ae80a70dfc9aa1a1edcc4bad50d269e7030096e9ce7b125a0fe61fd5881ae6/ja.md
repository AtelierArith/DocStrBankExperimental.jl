```
aws_event_stream_read_headers_from_buffer(headers, buffer, headers_len)
```

バッファからヘッダーを取得し、それらをヘッダーリストに格納します。リストのクリーンアップはユーザーの責任です。ここではバッファのコピーは行われず、バッファのライフタイムはヘッダーの使用よりも長くなければなりません。公開インターフェースで定義されたエラーコードを返します。

### プロトタイプ

```c
int aws_event_stream_read_headers_from_buffer( struct aws_array_list *headers, const uint8_t *buffer, size_t headers_len);
```
