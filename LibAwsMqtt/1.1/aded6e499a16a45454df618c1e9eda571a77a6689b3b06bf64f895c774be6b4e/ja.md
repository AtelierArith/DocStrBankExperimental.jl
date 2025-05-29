```
aws_mqtt_client_connection_get_stats(connection, stats)
```

接続の内部統計を不完全/未確認の操作について照会します。

# 引数

  * `connection`: 統計を取得する接続
  * `stats`: 不完全/未確認の操作統計のセット

# 戻り値

操作統計の取得が成功した場合は AWS*OP*SUCCESS、そうでない場合は AWS*OP*ERR

### プロトタイプ

```c
int aws_mqtt_client_connection_get_stats( struct aws_mqtt_client_connection *connection, struct aws_mqtt_connection_operation_statistics *stats);
```
