```
aws_iotdevice_defender_config_register_string_list_metric(task_config, metric_name, supplier, userdata)
```

デバイスディフェンダーのタスク設定に文字列リストのカスタムメトリックを追加します。設定を使用してすでに開始されているディフェンダータスクには影響を与えません。

# 引数

  * `task_config`:[in] メトリックを登録するディフェンダータスクの設定
  * `metric_name`:[in] メトリック名のUTF8バイト文字列
  * `supplier`:[in] レポート生成時にメトリック値を生成するためのコールバック関数
  * `userdata`:[in] サプライヤコールバック関数の特定のコールバックデータ

### プロトタイプ

```c
void aws_iotdevice_defender_config_register_string_list_metric( struct aws_iotdevice_defender_task_config *task_config, const struct aws_byte_cursor *metric_name, aws_iotdevice_defender_get_string_list_fn *supplier, void *userdata);
```
