```
aws_http_message_new_request(allocator)
```

新しいHTTP/1.1リクエストメッセージを作成します。メッセージは空白であり、すべてのプロパティ（メソッド、パスなど）は個別に設定する必要があります。HTTP/1.1メッセージがHTTP/2接続で使用される場合、変換は自動的に適用されます。HTTP/2メッセージは、HTTP/1.1メッセージに基づいて作成され、送信されます。

呼び出し元はオブジェクトを保持しており、使用が完了したら[`aws_http_message_release`](@ref)()を呼び出す必要があります。

### プロトタイプ

```c
struct aws_http_message *aws_http_message_new_request(struct aws_allocator *allocator);
```
