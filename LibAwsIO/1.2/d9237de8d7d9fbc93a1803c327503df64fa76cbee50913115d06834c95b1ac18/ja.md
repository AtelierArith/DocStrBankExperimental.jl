```
testing_channel_get_read_message_queue(testing)
```

ハンドラーの読み取り出力をテストしたいときは、これを呼び出し、キューを取得してメッセージを反復処理します。ダウンストリームハンドラーがインストールされている必要があります。

### プロトタイプ

```c
static inline struct aws_linked_list *testing_channel_get_read_message_queue(struct testing_channel *testing);
```
