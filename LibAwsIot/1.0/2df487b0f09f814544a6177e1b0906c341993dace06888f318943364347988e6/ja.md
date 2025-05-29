```
aws_iotdevice_defender_task_create_ex(task_out, config, publish_fn, event_loop)
```

デバイスディフェンダーのレポートタスクを作成し、開始します。このタスクがレポートを公開する必要があるときに、各レポートを受け入れ/処理する関数を定義する能力があります。

# 引数

  * `task_out`:[out] ディフェンダータスクを指すように設定する出力パラメータ
  * `config`:[in] タスクを開始するために使用するディフェンダータスクの構成
  * `publish_fn`:[in] タスクによって生成されたレポートを処理するためのコールバック。ユーザーデータはタスク構成から来ます
  * `event_loop`:[in] レポートを公開するMQTTトピックを決定し、受け入れられたまたは拒否された応答をリッスンするために使用されるIoTデバイスのThing名

# 戻り値

タスクが正常に作成され、実行される予定であればAWS*OP*SUCCESS

### プロトタイプ

```c
int aws_iotdevice_defender_task_create_ex( struct aws_iotdevice_defender_task **task_out, const struct aws_iotdevice_defender_task_config *config, aws_iotdevice_defender_publish_fn *publish_fn, struct aws_event_loop *event_loop);
```
