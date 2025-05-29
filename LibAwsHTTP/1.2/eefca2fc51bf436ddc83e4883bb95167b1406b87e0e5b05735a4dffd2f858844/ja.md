```
aws_http1_stream_add_chunked_trailer(http1_stream, trailing_headers)
```

最後のチャンクが送信された後に送信されるトレーリングヘッダーとして追加されるヘッダーのリストを追加します。"Trailer" ヘッダーフィールドは、トレーラーに存在するフィールドを示します。

特定のヘッダーはトレーラーにおいて禁止されています（例：Transfer-Encoding、Content-Length、Host）。詳細についてはRFC-7541のセクション4.1.2を参照してください。

クライアントストリームの場合、チャンクが送信される前にactivate()を呼び出す必要があります。

サーバーストリームの場合、トレーラーを追加する前にレスポンスを送信する必要があります。

[`aws_http1_stream_add_chunked_trailer`](@ref)は、最終サイズ0のチャンクの前に呼び出す必要があり、現時点では一度だけ呼び出すことができますが、必要に応じて変更される可能性があります。

チャンクが送信された場合、AWS*OP*SUCCESSを返します。

### プロトタイプ

```c
int aws_http1_stream_add_chunked_trailer( struct aws_http_stream *http1_stream, const struct aws_http_headers *trailing_headers);
```
