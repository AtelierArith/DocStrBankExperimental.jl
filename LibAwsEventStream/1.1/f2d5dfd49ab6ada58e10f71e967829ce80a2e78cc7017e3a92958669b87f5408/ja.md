```
aws_event_stream_library_clean_up()
```

aws-c-event-streamで使用される内部データ構造をクリーンアップします。aws-c-event-streamの機能を使用しているアプリケーションが完了するまで呼び出してはいけません。

### プロトタイプ

```c
void aws_event_stream_library_clean_up(void);
```
