```
aws_mqtt_client_connection_publish(connection, topic, qos, retain, payload, on_complete, userdata)
```

接続を介してPUBLISHパケットを送信します。

# 引数

  * `connection`:[in] 公開する接続
  * `topic`:[in] 公開するトピック
  * `qos`:[in] パケットの要求されたQoS
  * `retain`:[in] サーバーにパケットを保存させ、トピックに一致するすべての新しいサブスクリプションに送信するにはTrue
  * `payload`:[in] 公開のペイロードとして送信するデータ
  * `on_complete`:[in](nullable) QoS 0の場合、パケットが送信されるとすぐに呼び出されます。QoS 1の場合、PUBACKを受信したときに呼び出されます。QoS 2の場合、PUBCOMPを受信したときに呼び出されます。
  * `user_data`:[in](nullable) on_completeに渡されます

# 戻り値

正常に送信された場合は公開パケットのパケットID、そうでない場合は0。

### プロトタイプ

```c
uint16_t aws_mqtt_client_connection_publish( struct aws_mqtt_client_connection *connection, const struct aws_byte_cursor *topic, enum aws_mqtt_qos qos, bool retain, const struct aws_byte_cursor *payload, aws_mqtt_op_complete_fn *on_complete, void *userdata);
```
