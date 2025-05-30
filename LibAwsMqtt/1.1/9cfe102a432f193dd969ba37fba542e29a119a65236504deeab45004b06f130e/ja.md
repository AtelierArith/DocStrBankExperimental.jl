```
aws_mqtt5_client_publish(client, publish_options, completion_options)
```

mqtt5 クライアントで Publish 操作をキューに追加します

# 引数

  * `client`: Publish のためにキューに追加する mqtt5 クライアント
  * `publish_options`: Publish 操作のための設定オプション
  * `completion_options`: 完了コールバックの設定。成功した QoS 0 の Publish は、データがソケットに書き込まれたときにコールバックを呼び出します。成功した QoS1+ の Publish は、対応する ack が受信されたときにコールバックを呼び出します。失敗した Publish は、失敗条件に達した時点でコールバックを呼び出します。

# 戻り値

Publish 操作を開始する同期ロジックにおける成功/失敗

### プロトタイプ

```c
int aws_mqtt5_client_publish( struct aws_mqtt5_client *client, const struct aws_mqtt5_packet_publish_view *publish_options, const struct aws_mqtt5_publish_completion_options *completion_options);
```
