```
aws_mqtt_client_connection_new_from_mqtt5_client(client)
```

MQTT5クライアントを内部で使用する新しいMQTT311接続オブジェクトを作成します。

# 引数

  * `client`:[in] 接続を作成するためのmqtt5クライアント

# 戻り値

成功した場合は新しいmqtt (311)接続、そうでない場合はNULL

### プロトタイプ

```c
struct aws_mqtt_client_connection *aws_mqtt_client_connection_new_from_mqtt5_client(struct aws_mqtt5_client *client);
```
