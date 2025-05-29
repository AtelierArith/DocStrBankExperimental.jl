```
testing_channel_push_read_message(testing, message)
```

ハンドラーの読み取りパスをテストしたいときは、読み取ってほしいメッセージを使ってこれを呼び出します。

### プロトタイプ

```c
static inline int testing_channel_push_read_message(struct testing_channel *testing, struct aws_io_message *message);
```
