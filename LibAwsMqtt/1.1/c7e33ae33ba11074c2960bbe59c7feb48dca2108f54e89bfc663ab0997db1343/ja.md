```
aws_mqtt_client_connection_set_reconnect_timeout(connection, min_timeout, max_timeout)
```

最小および最大の再接続タイムアウトを設定します。

再接続試行の間隔は、最初は最小値から始まり、最大値に達するまで2倍に増加します。

# 引数

  * `connection`:[in] 接続オブジェクト
  * `min_timeout`:[in] 開始するタイムアウト
  * `max_timeout`:[in] 再接続試行の間の最長許容待機時間

### プロトタイプ

```c
int aws_mqtt_client_connection_set_reconnect_timeout( struct aws_mqtt_client_connection *connection, uint64_t min_timeout, uint64_t max_timeout);
```
