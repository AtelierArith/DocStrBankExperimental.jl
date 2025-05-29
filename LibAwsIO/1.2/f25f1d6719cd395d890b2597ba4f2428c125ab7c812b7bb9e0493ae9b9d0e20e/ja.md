```
testing_channel_push_write_message(testing, message)
```

ハンドラーの書き込みパスをテストしたいときは、書き込みたいメッセージを使ってこれを呼び出します。ダウンストリームハンドラーがインストールされている必要があります。

### プロトタイプ

```c
static inline int testing_channel_push_write_message(struct testing_channel *testing, struct aws_io_message *message);
```
