```
aws_iotdevice_defender_config_set_report_accepted_fn(config, accepted_fn)
```

キャンセルされたときに呼び出されるレポート拒否コールバック関数を設定します。これは、タスクが実行中に保持されているリソースを閉じたり解放したりするのが適切なタイミングの提案です。

# 引数

  * `config`:[in] ディフェンダータスクの設定
  * `accepted_fn`:[in] 受け入れられたレポートコールバック関数

# 戻り値

レポート受け入れコールバックが設定された場合は AWS*OP*SUCCESS を返します。コールバックが設定されなかった場合はエラーを返します。

### プロトタイプ

```c
int aws_iotdevice_defender_config_set_report_accepted_fn( struct aws_iotdevice_defender_task_config *config, aws_iotdevice_defender_report_accepted_fn *accepted_fn);
```
