```
aws_http_stream_update_window(stream, increment_size)
```

ストリームのフロー制御ウィンドウを増加させてデータの流れを維持します。

`manual_window_management`がtrueに設定されている場合、ボディデータが受信されると各ストリームのフロー制御ウィンドウは縮小します（ヘッダー、パディング、およびその他のメタデータはウィンドウに影響を与えません）。接続の`initial_window_size`は各ストリームのウィンドウの開始サイズを決定します。ストリームのフロー制御ウィンドウが0に達すると、これ以上のデータは受信されません。

`manual_window_management`がfalseの場合、この呼び出しは効果がありません。接続はフロー制御ウィンドウを維持し、バックプレッシャーがかからないようにし、データが可能な限り速く到着するようにします。

HTTP/2の場合、クライアントはWINDOW*UPDATEフレームが送信される正確なタイミングを制御します。そしてクライアントはWINDOW*UPDATEフレームが有効であることを確認します。詳細については`stream_window_size_threshold_to_send_update`を確認してください。

### プロトタイプ

```c
void aws_http_stream_update_window(struct aws_http_stream *stream, size_t increment_size);
```
