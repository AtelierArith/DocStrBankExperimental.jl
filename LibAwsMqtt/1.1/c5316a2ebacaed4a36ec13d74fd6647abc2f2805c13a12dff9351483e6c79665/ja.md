```
aws_mqtt_client_connection_unsubscribe(connection, topic_filter, on_unsuback, on_unsuback_ud)
```

トピックフィルターの購読を解除します。

# 引数

  * `connection`:[in] 購読解除する接続
  * `topic_filter`:[in] 購読解除するトピックフィルター。このリソースはon_unsubackまで保持する必要があります。
  * `on_unsuback`:[in](nullable) サーバーからUNSUBACKが受信され、購読が解除されたときに呼び出されます
  * `on_unsuback_ud`:[in](nullable) on_unsubackに渡されます

# 戻り値

正常に送信された場合は購読解除パケットのパケットID、そうでない場合は0。

### プロトタイプ

```c
uint16_t aws_mqtt_client_connection_unsubscribe( struct aws_mqtt_client_connection *connection, const struct aws_byte_cursor *topic_filter, aws_mqtt_op_complete_fn *on_unsuback, void *on_unsuback_ud);
```
