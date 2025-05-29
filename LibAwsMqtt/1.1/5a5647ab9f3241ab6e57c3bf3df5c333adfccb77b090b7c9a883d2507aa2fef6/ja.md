```
aws_mqtt_client_connection_set_host_resolution_options(connection, host_resolution_config)
```

接続のホスト解決オプションを設定します。

### プロトタイプ

```c
int aws_mqtt_client_connection_set_host_resolution_options( struct aws_mqtt_client_connection *connection, const struct aws_host_resolution_config *host_resolution_config);
```
