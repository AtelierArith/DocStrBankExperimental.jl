```
aws_http_headers_new(allocator)
```

新しいヘッダーオブジェクトを作成します。呼び出し元はオブジェクトを保持しており、使用が完了したら[`aws_http_headers_release`](@ref)()を呼び出す必要があります。

### プロトタイプ

```c
struct aws_http_headers *aws_http_headers_new(struct aws_allocator *allocator);
```
