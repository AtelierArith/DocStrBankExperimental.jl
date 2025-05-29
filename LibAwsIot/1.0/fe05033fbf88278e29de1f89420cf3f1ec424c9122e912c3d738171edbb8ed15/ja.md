```
aws_iotdevice_defender_config_create(config_out, allocator, thing_name, report_format)
```

Device Defender メトリクス収集のための新しい報告タスク設定を作成します

# 引数

  * `config_out`:[in] タスク設定へのポインタを書き込む出力。タスク設定の作成に成功した場合は非NULLを書き込みます。作成中にエラーが発生した場合はNULLを書き込みます
  * `allocator`:[in] タスク設定の内部データおよびタスク自体を開始する際に使用するアロケータ
  * `thing_name`:[in] タスク設定が報告するためのThing名
  * `report_format`:[in] IoTに公開する際に生成する報告フォーマット

# 戻り値

AWS*OP*SUCCESS および config_out は非NULLになります。それ以外の場合はエラーコードを返します

### プロトタイプ

```c
int aws_iotdevice_defender_config_create( struct aws_iotdevice_defender_task_config **config_out, struct aws_allocator *allocator, const struct aws_byte_cursor *thing_name, enum aws_iotdevice_defender_report_format report_format);
```
