```
aws_iotdevice_defender_config_set_report_rejected_fn(config, rejected_fn)
```

キャンセルされたときに呼び出される報告拒否コールバック関数を設定します。これは、タスクが実行中に保持されているリソースを閉じたり解放したりするのが適切なタイミングの提案です。

# 引数

  * `config`:[in] ディフェンダータスクの設定
  * `rejected_fn`:[in] 拒否された報告のコールバック関数

# 戻り値

報告拒否コールバックが設定された場合は AWS*OP*SUCCESS を返します。コールバックが設定されなかった場合はエラーを返します。

### プロトタイプ

```c
int aws_iotdevice_defender_config_set_report_rejected_fn( struct aws_iotdevice_defender_task_config *config, aws_iotdevice_defender_report_rejected_fn *rejected_fn);
```
