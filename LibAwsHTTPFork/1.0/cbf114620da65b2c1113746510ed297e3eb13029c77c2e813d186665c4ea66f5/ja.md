```
aws_http2_message_new_response(allocator)
```

新しいHTTP/2レスポンスメッセージを作成します。擬似ヘッダーは[`aws_http2_headers_set_response_status`](@ref)から[`aws_http_message`](@ref)のヘッダーに設定する必要があります。HTTP/1.1接続で使用された場合はエラーになります。

呼び出し元はオブジェクトを保持しており、使用が完了したら[`aws_http_message_release`](@ref)()を呼び出す必要があります。

### プロトタイプ

```c
struct aws_http_message *aws_http2_message_new_response(struct aws_allocator *allocator);
```
