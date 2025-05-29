```
aws_mqtt_client_acquire(client)
```

mqttクライアントの参照カウントを増加させ、呼び出し元がそれを参照できるようにします。

# 引数

  * `client`:[in] 参照カウントを増加させるクライアント

# 戻り値

mqttクライアント

### プロトタイプ

```c
struct aws_mqtt_client *aws_mqtt_client_acquire(struct aws_mqtt_client *client);
```
