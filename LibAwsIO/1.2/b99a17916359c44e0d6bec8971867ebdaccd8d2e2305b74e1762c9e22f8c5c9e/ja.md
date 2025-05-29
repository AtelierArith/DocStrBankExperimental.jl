```
testing_channel_get_written_message_queue(testing)
```

ハンドラーの書き出し出力をテストしたいときは、これを呼び出し、キューを取得してメッセージを反復処理します。

### プロトタイプ

```c
static inline struct aws_linked_list *testing_channel_get_written_message_queue(struct testing_channel *testing);
```
