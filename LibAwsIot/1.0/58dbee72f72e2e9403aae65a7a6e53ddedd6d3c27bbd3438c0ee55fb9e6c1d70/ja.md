```
aws_iotdevice_defender_config_set_task_failure_fn(config, failure_fn)
```

タスクの実行中に失敗が発生した場合に呼び出されるタスク失敗コールバック関数を設定します。これは指定することがオプションですが、タスクの実行を停止させる失敗を少なくとも監視するためにハンドラーを登録することが重要です。

タスクが継続できない最も可能性の高いシナリオは、タスクを再スケジュールできないことです。

# 引数

  * `config`:[in] ディフェンダータスクの設定
  * `failure_fn`:[in] 失敗コールバック関数

# 戻り値

タスク失敗コールバックが設定された場合は AWS*OP*SUCCESS を返します。コールバックが設定されていない場合はエラーを返します。

### プロトタイプ

```c
int aws_iotdevice_defender_config_set_task_failure_fn( struct aws_iotdevice_defender_task_config *config, aws_iotdevice_defender_task_failure_fn *failure_fn);
```
