```
aws_http2_connection_get_received_goaway(http2_connection, out_http2_error, out_last_stream_id)
```

ピアから受信した最新のGOAWAYフレームに関するデータを取得します（HTTP/2のみ）。GOAWAYが受信されていない場合、またはGOAWAYペイロードがまだ送信中の場合、AWS*ERROR*HTTP*DATA*NOT_AVAILABLEが発生します。

# 引数

  * `http2_connection`: HTTP/2接続。
  * `out_http2_error`: 最新のGOAWAYで受信したHTTP/2エラーコードに設定されます。
  * `out_last_stream_id`: 最新のGOAWAYで受信したLast-Stream-IDに設定されます。

### プロトタイプ

```c
int aws_http2_connection_get_received_goaway( struct aws_http_connection *http2_connection, uint32_t *out_http2_error, uint32_t *out_last_stream_id);
```
