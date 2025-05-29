```
aws_iotdevice_defender_task_clean_up(defender_task)
```

デバイスディフェンダーのメトリクスを報告する実行中のタスクをキャンセルし、クリーンアップします。タスクが現在実行中の場合、タスクがキャンセルされ、正常にクリーンアップされるまでブロックします。

# 引数

  * `defender_task`:[in] 停止してクリーンアップする実行中のタスク

### プロトタイプ

```c
void aws_iotdevice_defender_task_clean_up(struct aws_iotdevice_defender_task *defender_task);
```
