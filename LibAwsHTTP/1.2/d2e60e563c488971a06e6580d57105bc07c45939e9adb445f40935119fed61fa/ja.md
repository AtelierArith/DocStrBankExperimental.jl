```
aws_http1_stream_write_chunk(http1_stream, options)
```

HTTP/1.1 ストリームに送信されるデータのチャンクを提出します。ストリームは「transfer-encoding」ヘッダーに「chunked」を指定している必要があり、[`aws_http_message`](@ref) はボディストリームが設定されていない必要があります。クライアントストリームの場合、チャンクが提出される前に activate() を呼び出す必要があります。サーバーストリームの場合、チャンクが提出される前にレスポンスを提出する必要があります。HTTPストリームを正常に完了させるには、サイズ0の最終チャンクを提出する必要があります。

チャンクが提出された場合、AWS*OP*SUCCESS を返します。チャンクの完了コールバックは、HTTPストリームがチャンクデータを処理し終えたときに呼び出されます。成功裏に送信されたかどうかにかかわらず（[`aws_http1_stream_write_chunk_complete_fn`](@ref) を参照）。チャンクデータは、完了コールバックが呼び出されるまで有効である必要があります。

チャンクが提出できなかった場合、AWS*OP*ERR を返し、エラーを発生させます。この場合、チャンクの完了コールバックは決して呼び出されません。この呼び出しが行われる前に、HTTPストリームが予期せず終了する可能性が常にあることに注意してください。この場合、発生するエラーは AWS*ERROR*HTTP*STREAM*HAS_COMPLETED です。

### プロトタイプ

```c
int aws_http1_stream_write_chunk( struct aws_http_stream *http1_stream, const struct aws_http1_chunk_options *options);
```
