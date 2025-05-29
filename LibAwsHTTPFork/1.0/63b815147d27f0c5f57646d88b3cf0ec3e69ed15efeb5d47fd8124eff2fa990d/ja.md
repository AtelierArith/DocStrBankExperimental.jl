```
aws_http_message_new_response(allocator)
```

新しいHTTP/1.1レスポンスメッセージを作成します。メッセージは空であり、すべてのプロパティ（ステータス、ヘッダーなど）は個別に設定する必要があります。

呼び出し元はオブジェクトを保持しており、使用が完了したら[`aws_http_message_release`](@ref)()を呼び出す必要があります。

### プロトタイプ

```c
struct aws_http_message *aws_http_message_new_response(struct aws_allocator *allocator);
```
