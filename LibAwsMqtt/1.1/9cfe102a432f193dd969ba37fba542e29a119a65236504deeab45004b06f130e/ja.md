```
aws_mqtt5_client_publish(client, publish_options, completion_options)
```

mqtt5クライアントでPublish操作をキューに追加します

# 引数

  * `client`: Publishのためにキューに追加するmqtt5クライアント
  * `publish_options`: Publish操作のための設定オプション
  * `completion_options`: 完了コールバックの設定。成功したQoS 0のPublishは、データがソケットに書き込まれたときにコールバックを呼び出します。成功したQoS1+のPublishは、対応するackが受信されたときにコールバックを呼び出します。失敗したPublishは、失敗条件に達した時点でコールバックを呼び出します。

# 戻り値

Publish操作を開始する同期ロジックにおける成功/失敗

### プロトタイプ

```c
int aws_mqtt5_client_publish( struct aws_mqtt5_client *client, const struct aws_mqtt5_packet_publish_view *publish_options, const struct aws_mqtt5_publish_completion_options *completion_options);
```
