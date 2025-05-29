```
aws_mqtt_client_connection_disconnect(connection, on_disconnect, userdata)
```

接続を非同期に閉じ、on*disconnect コールバックを呼び出します。すべての未完了のリクエスト（publish/subscribe/unsubscribe）は、clean*session の状態に関係なくキャンセルされます。DISCONNECT パケットが送信され、サーバーからウィルメッセージが削除されます。

# 引数

  * `connection`:[in] 閉じる接続
  * `on_disconnect`:[in](nullable) 接続が完全に切断されたときに呼び出されるコールバック関数。
  * `userdata`:[in](nullable) on_disconnect に渡される

# 戻り値

接続がオープンでシャットダウン中であれば AWS*OP*SUCCESS、それ以外の場合は AWS*OP*ERR で aws*last*error() が設定されます。

### プロトタイプ

```c
int aws_mqtt_client_connection_disconnect( struct aws_mqtt_client_connection *connection, aws_mqtt_client_on_disconnect_fn *on_disconnect, void *userdata);
```
