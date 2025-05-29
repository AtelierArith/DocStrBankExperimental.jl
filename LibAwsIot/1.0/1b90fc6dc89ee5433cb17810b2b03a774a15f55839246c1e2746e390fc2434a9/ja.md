```
aws_iotdevice_defender_task_create(task_out, config, connection, event_loop)
```

新しいデバイスディフェンダー報告タスクを作成して開始します

# 引数

  * `task_out`:[out] ディフェンダータスクを指すように設定する出力パラメータ
  * `config`:[in] タスクを開始するために使用するディフェンダータスクの構成
  * `connection`:[in] レポートを公開するために使用するmqtt接続
  * `event_loop`:[in] レポートを公開するMQTTトピックを決定し、受け入れられたまたは拒否された応答をリッスンするために使用されるIoTデバイスのThing名

# 戻り値

タスクが正常に作成され、実行される予定であればAWS*OP*SUCCESS

### プロトタイプ

```c
int aws_iotdevice_defender_task_create( struct aws_iotdevice_defender_task **task_out, const struct aws_iotdevice_defender_task_config *config, struct aws_mqtt_client_connection *connection, struct aws_event_loop *event_loop);
```
