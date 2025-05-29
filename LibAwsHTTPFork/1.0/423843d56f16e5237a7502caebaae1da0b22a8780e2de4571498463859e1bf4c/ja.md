```
aws_http2_message_new_from_http1(alloc, http1_msg)
```

HTTP/1.1 メッセージから HTTP/2 メッセージを作成します。擬似ヘッダーはコンテキストから作成され、新しいメッセージのヘッダーに追加されます。通常のヘッダーは新しいメッセージのヘッダーにコピーされます。注意: - `host` が存在する場合、それは削除され、`:authority` が情報を使用して追加されます。 - `:scheme` は常に "https" にデフォルト設定されます。異なるスキームを使用するには、HTTP/2 メッセージを直接作成してください。

### プロトタイプ

```c
struct aws_http_message *aws_http2_message_new_from_http1( struct aws_allocator *alloc, const struct aws_http_message *http1_msg);
```
