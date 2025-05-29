```
aws_iotdevice_defender_config_set_task_cancelation_fn(config, cancel_fn)
```

タスクがキャンセルされ、実行される予定がないときに呼び出されるタスクキャンセルコールバック関数を設定します。これは、タスクが実行中に保持されているリソースを閉じたり解放したりするのが許可されるタイミングの提案です。

# 引数

  * `config`:[in] ディフェンダータスクの設定
  * `cancel_fn`:[in] キャンセルコールバック関数

# 戻り値

タスクキャンセルコールバックが設定された場合は AWS*OP*SUCCESS を返します。コールバックが設定されなかった場合はエラーを返します。

### プロトタイプ

```c
int aws_iotdevice_defender_config_set_task_cancelation_fn( struct aws_iotdevice_defender_task_config *config, aws_iotdevice_defender_task_canceled_fn *cancel_fn);
```
