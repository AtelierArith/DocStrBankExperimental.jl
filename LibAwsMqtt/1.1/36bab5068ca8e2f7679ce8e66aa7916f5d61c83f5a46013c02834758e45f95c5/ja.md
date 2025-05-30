```
aws_mqtt_client_connection_set_will(connection, topic, qos, retain, payload)
```

接続パケットと共に送信するウィルメッセージを設定します。

# 引数

  * `connection`:[in] 接続オブジェクト
  * `topic`:[in] ウィルを公開するトピック
  * `qos`:[in] ウィルを公開する際のQoS
  * `retain`:[in] ウィルを公開する際の保持フラグ
  * `payload`:[in] ウィルメッセージのデータ

### プロトタイプ

```c
int aws_mqtt_client_connection_set_will( struct aws_mqtt_client_connection *connection, const struct aws_byte_cursor *topic, enum aws_mqtt_qos qos, bool retain, const struct aws_byte_cursor *payload);
```
