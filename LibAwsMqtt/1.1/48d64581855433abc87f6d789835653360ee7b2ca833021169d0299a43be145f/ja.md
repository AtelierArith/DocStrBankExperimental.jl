```
aws_mqtt_client_connection_reconnect(connection, on_connection_complete, userdata)
```

非推奨 [`aws_mqtt_client_connection_new`](@ref) で定義された実際の接続を開きます。接続が開かれると、on_connack が呼び出されます。

以前に開かれた接続で呼び出す必要があり、最後の接続時に渡されたパラメータが再利用されます。

# 引数

  * `connection`:[in] 接続オブジェクト
  * `on_connection_complete`:[in] 接続試行が完了したときに呼び出されるコールバック
  * `userdata`:[in](nullable) on*connection*complete の userdata パラメータに渡される

# 戻り値

接続が正常に開始された場合は AWS*OP*SUCCESS、それ以外の場合は AWS*OP*ERR が返され、aws*last*error() が設定されます。

### プロトタイプ

```c
int aws_mqtt_client_connection_reconnect( struct aws_mqtt_client_connection *connection, aws_mqtt_client_on_connection_complete_fn *on_connection_complete, void *userdata);
```
