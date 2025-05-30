```
aws_mqtt5_client_stop(client, disconnect_options, completion_options)
```

非同期的にmqtt5クライアントに停止状態に遷移するよう通知します。クライアントが停止状態に達すると、すべてのセッション状態が消去されます。

# 引数

  * `client`: 停止するmqtt5クライアント
  * `disconnect_options`: (オプション) シャットダウンプロセスの一部として送信するDISCONNECTパケットのプロパティ

# 戻り値

停止プロセスを開始する同期ロジックにおける成功/失敗

### プロトタイプ

```c
int aws_mqtt5_client_stop( struct aws_mqtt5_client *client, const struct aws_mqtt5_packet_disconnect_view *disconnect_options, const struct aws_mqtt5_disconnect_completion_options *completion_options);
```
