```
aws_iotdevice_defender_config_set_task_period_ns(config, task_period_ns)
```

デバイスディフェンダータスクの期間を設定します

# 引数

  * `config`:[in] ディフェンダータスクの設定
  * `task_period_ns`:[in] ディフェンダータスクの実行間隔（ナノ秒単位）

# 戻り値

プロパティが正しく設定された場合は AWS*OP*SUCCESS を返します。値を設定できなかった場合はエラーコードを返します。

### プロトタイプ

```c
int aws_iotdevice_defender_config_set_task_period_ns( struct aws_iotdevice_defender_task_config *config, uint64_t task_period_ns);
```
