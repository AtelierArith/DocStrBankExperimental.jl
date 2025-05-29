```
aws_http2_message_new_request(allocator)
```

新しいHTTP/2リクエストメッセージを作成します。擬似ヘッダーは[`aws_http_message`](@ref)のヘッダーに対してaws*http2*headers*set*request_*から設定する必要があります。HTTP/1.1接続で使用された場合はエラーになります。

呼び出し元はオブジェクトを保持しており、使用が完了したら[`aws_http_message_release`](@ref)()を呼び出す必要があります。

### プロトタイプ

```c
struct aws_http_message *aws_http2_message_new_request(struct aws_allocator *allocator);
```
