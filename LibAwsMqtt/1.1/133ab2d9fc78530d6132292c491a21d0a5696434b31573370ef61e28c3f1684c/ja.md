```
aws_mqtt5_client_get_stats(client, stats)
```

クライアントの内部統計を不完全な操作について照会します。

# 引数

  * `client`: 統計を取得するクライアント
  * `stats`: 不完全な操作の統計のセット

### プロトタイプ

```c
void aws_mqtt5_client_get_stats(struct aws_mqtt5_client *client, struct aws_mqtt5_client_operation_statistics *stats);
```
