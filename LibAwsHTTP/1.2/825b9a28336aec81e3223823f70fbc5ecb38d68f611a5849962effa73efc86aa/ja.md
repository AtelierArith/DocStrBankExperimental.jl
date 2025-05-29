```
aws_http2_connection_get_sent_goaway(http2_connection, out_http2_error, out_last_stream_id)
```

ピアに送信された最新のGOAWAYフレームに関するデータを取得します（HTTP/2のみ）。GOAWAYが送信されていない場合、AWS*ERROR*HTTP*DATA*NOT_AVAILABLEが発生します。GOAWAYフレームは、通常、接続がシャットダウン中に自動的に送信されることに注意してください。

# 引数

  * `http2_connection`: HTTP/2接続。
  * `out_http2_error`: 最も最近のGOAWAYで送信されたHTTP/2エラーコードに設定されます。
  * `out_last_stream_id`: 最も最近のGOAWAYで送信されたLast-Stream-IDに設定されます。

### プロトタイプ

```c
int aws_http2_connection_get_sent_goaway( struct aws_http_connection *http2_connection, uint32_t *out_http2_error, uint32_t *out_last_stream_id);
```
