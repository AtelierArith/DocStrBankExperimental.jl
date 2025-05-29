```
aws_iotdevice_defender_config_set_callback_userdata(config, userdata)
```

デバイスディフェンダータスクのコールバック関数のためのユーザーデータを設定します

# 引数

  * `config`:[in] ディフェンダータスクの設定
  * `userdata`:[in] ディフェンダータスクの実行間隔（ナノ秒単位）

# 戻り値

プロパティが正しく設定された場合は AWS*OP*SUCCESS を返します。値を設定できなかった場合はエラーコードを返します

### プロトタイプ

```c
int aws_iotdevice_defender_config_set_callback_userdata( struct aws_iotdevice_defender_task_config *config, void *userdata);
```
