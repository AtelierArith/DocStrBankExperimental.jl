```
aws_http2_stream_write_data(http2_stream, options)
```

ストリームはリクエスト作成時に `http2_use_manual_data_writes` を指定する必要があります。クライアントストリームの場合、フレームが送信される前に activate() を呼び出す必要があります。サーバーストリームの場合、フレームが送信される前にレスポンスヘッダーを送信する必要があります。end_stream が true に設定されたオプションでの書き込みはストリームを終了させ、さらなる書き込みを防ぎます。

典型的な使用法は次のようになります: options.http2*use*manual*data*writes = true; stream = [`aws_http_connection_make_request`](@ref)(connection, &options); [`aws_http_stream_activate`](@ref)(stream); ... 構造体 [`aws_http2_stream_write_data_options`](@ref) write; [`aws_http2_stream_write_data`](@ref)(stream, &write); ... 構造体 [`aws_http2_stream_write_data_options`](@ref) last*write; last*write.end*stream = true; [`aws*http2*stream*write*data`](@ref)(stream, &write); ... [`aws*http*stream*release`](@ref)(stream);

# 戻り値

書き込みがキューに追加された場合は AWS*OP*SUCCESS、試行がエラーコードを引き起こした場合は AWS*OP*ERROR。無効な使用に対しては AWS*ERROR*INVALID*STATE が発生します。裏での理由でストリームが終了した場合は AWS*ERROR*HTTP*STREAM*HAS*COMPLETED が発生します。

### プロトタイプ

```c
int aws_http2_stream_write_data( struct aws_http_stream *http2_stream, const struct aws_http2_stream_write_data_options *options);
```
