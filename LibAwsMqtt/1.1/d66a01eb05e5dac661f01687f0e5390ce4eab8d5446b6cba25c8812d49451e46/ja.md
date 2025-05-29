```
aws_mqtt_client_connection_subscribe(connection, topic_filter, qos, on_publish, on_publish_ud, on_ud_cleanup, on_suback, on_suback_ud)
```

単一のトピックフィルターにサブスクライブします。on*publishは、topic*filterに一致するPUBLISHが受信されたときに呼び出されます。

# 引数

  * `connection`:[in] サブスクライブする接続
  * `topic_filter`:[in] サブスクライブするトピックフィルター。このリソースはon_subackまで持続する必要があります。
  * `qos`:[in] 受信するメッセージの最大QoS
  * `on_publish`:[in](nullable) topic_filterに一致するPUBLISHパケットが受信されたときに呼び出されます
  * `on_publish_ud`:[in](nullable) on_publishに渡されます
  * `on_ud_cleanup`:[in](nullable) サブスクリプションが削除されたときに呼び出され、on*publish*udが渡されます。
  * `on_suback`:[in](nullable) サーバーからSUBACKが受信され、サブスクリプションが完了したときに呼び出されます
  * `on_suback_ud`:[in](nullable) on_subackに渡されます

# 戻り値

サブスクライブパケットのパケットIDが正常に送信された場合はそれを返し、そうでない場合は0を返します。

### プロトタイプ

```c
uint16_t aws_mqtt_client_connection_subscribe( struct aws_mqtt_client_connection *connection, const struct aws_byte_cursor *topic_filter, enum aws_mqtt_qos qos, aws_mqtt_client_publish_received_fn *on_publish, void *on_publish_ud, aws_mqtt_userdata_cleanup_fn *on_ud_cleanup, aws_mqtt_suback_fn *on_suback, void *on_suback_ud);
```
