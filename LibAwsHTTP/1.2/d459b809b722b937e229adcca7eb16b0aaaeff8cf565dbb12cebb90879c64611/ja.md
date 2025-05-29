```
aws_http2_connection_send_goaway(http2_connection, http2_error, allow_more_streams, optional_debug_data)
```

カスタムGOAWAYフレームを送信します（HTTP/2のみ）。

接続は、シャットダウン中に自動的にGOAWAYを送信しようとします（有効なLast-Stream-IDを持つGOAWAYがすでに送信されていない限り）。

この呼び出しは、接続の終了が迫っていることを相手に優雅に警告するために使用できます（http2*error=0、allow*more_streams=true）、またはこの接続によって送信される最終GOAWAYフレームをカスタマイズするために使用できます。

接続がすでに閉じている場合、相手側はgoawayを受信できないことがあります。

# 引数

  * `http2_connection`: HTTP/2接続。
  * `http2_error`: 送信するHTTP/2エラーコード（RFC-7540セクション7）。`enum [`aws*http2*error_code`](@ref)`は公式コードをリストします。
  * `allow_more_streams`: trueの場合、新しいピア起動のストリームは引き続き確認され、GOAWAYのLast-Stream-IDは最大値に設定されます。falseの場合、新しいピア起動のストリームは無視され、GOAWAYのLast-Stream-IDは最新の確認済みストリームに設定されます。
  * `optional_debug_data`: 送信するオプションのデバッグデータ。サイズは16KBを超えてはいけません。

### プロトタイプ

```c
void aws_http2_connection_send_goaway( struct aws_http_connection *http2_connection, uint32_t http2_error, bool allow_more_streams, const struct aws_byte_cursor *optional_debug_data);
```
