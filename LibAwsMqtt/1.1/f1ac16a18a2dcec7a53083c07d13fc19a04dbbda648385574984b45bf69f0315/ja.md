```
aws_mqtt_client_connection_connect(connection, connection_options)
```

[`aws_mqtt_client_connection_new`](@ref)で定義された実際の接続を開きます。接続が開かれると、on_connackが呼び出されます。接続が切断されたときのみ呼び出されます。

# 引数

  * `connection`:[in] 接続オブジェクト
  * `connection_options`:[in] 接続試行のための構成情報

# 戻り値

接続が正常に開始された場合はAWS*OP*SUCCESS、それ以外の場合はAWS*OP*ERRが返され、aws*last*error()が設定されます。

### プロトタイプ

```c
int aws_mqtt_client_connection_connect( struct aws_mqtt_client_connection *connection, const struct aws_mqtt_connection_options *connection_options);
```
