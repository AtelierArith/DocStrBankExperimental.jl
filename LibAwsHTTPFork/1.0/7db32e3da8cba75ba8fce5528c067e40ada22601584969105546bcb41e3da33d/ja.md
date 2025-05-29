```
aws_http2_connection_ping(http2_connection, optional_opaque_data, on_completed, user_data)
```

PINGフレームを送信します（HTTP/2のみ）。PING ACKがピアから受信されると、往復時間が計算されます。

# 引数

  * `http2_connection`: HTTP/2接続。
  * `optional_opaque_data`: PINGフレームのオプションペイロード。NULLであるか、正確に8バイト（[`AWS_HTTP2_PING_DATA_SIZE`](@ref)）でなければなりません。NULLの場合、8バイトのペイロードはすべてゼロになります。
  * `on_completed`: PING ACKがピアから受信されたとき、または接続エラーによりPING ACKが受信できない場合に呼び出されるオプションのコールバック。コールバックは常に接続のイベントループスレッドで発火します。
  * `user_data`: on_completedコールバックに渡すユーザーデータ。

### プロトタイプ

```c
int aws_http2_connection_ping( struct aws_http_connection *http2_connection, const struct aws_byte_cursor *optional_opaque_data, aws_http2_on_ping_complete_fn *on_completed, void *user_data);
```
