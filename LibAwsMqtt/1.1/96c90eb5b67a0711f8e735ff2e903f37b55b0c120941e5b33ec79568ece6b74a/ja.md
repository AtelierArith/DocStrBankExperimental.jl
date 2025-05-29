```
aws_mqtt_client_release(client)
```

MQTTクライアントの参照カウントを減少させます。参照カウントがゼロになると、クライアントはクリーンアップされます。

# 引数

  * `client`:[in] 参照カウントを解放するクライアント

### プロトタイプ

```c
void aws_mqtt_client_release(struct aws_mqtt_client *client);
```
