```
aws_mqtt_client_connection_release(connection)
```

MQTT接続の参照カウントを減少させます。参照カウントがゼロになると、接続がクリーンアップされます。注意: ロックを保持している状態でこの関数を呼び出すことはできません。なぜなら、破棄プロセスが開始され、デッドロックを引き起こす可能性があるからです。

# 引数

  * `connection`:[in] 接続オブジェクト

### プロトタイプ

```c
void aws_mqtt_client_connection_release(struct aws_mqtt_client_connection *connection);
```
