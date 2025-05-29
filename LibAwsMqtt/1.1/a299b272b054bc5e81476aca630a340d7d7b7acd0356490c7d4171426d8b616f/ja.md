```
aws_mqtt_client_connection_acquire(connection)
```

mqttクライアント接続の参照カウントを増加させ、呼び出し元がそれへの参照を取得できるようにします。

# 引数

  * `connection`:[in] 接続オブジェクト

# 戻り値

mqtt接続

### プロトタイプ

```c
struct aws_mqtt_client_connection *aws_mqtt_client_connection_acquire(struct aws_mqtt_client_connection *connection);
```
