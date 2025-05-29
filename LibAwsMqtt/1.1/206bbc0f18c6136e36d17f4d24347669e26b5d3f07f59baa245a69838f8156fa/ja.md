```
aws_mqtt_client_connection_new(client)
```

新しい接続オブジェクトを生成します。

# 引数

  * `client`:[in] 接続を生成するためのクライアント

# 戻り値

成功した場合は新しいmqtt接続、そうでない場合はNULL

### プロトタイプ

```c
struct aws_mqtt_client_connection *aws_mqtt_client_connection_new(struct aws_mqtt_client *client);
```
