```
testing_channel_set_downstream_handler_shutdown_callback(testing, on_shutdown, user_data)
```

ハンドラーのシャットダウン中に呼び出されるコールバックを設定します。読み取り方向で一度、書き込み方向で再度呼び出されます。これを使用して、チャネルのシャットダウンの途中で発生する可能性のあるアクションを注入します。

### プロトタイプ

```c
static inline void testing_channel_set_downstream_handler_shutdown_callback( struct testing_channel *testing, testing_channel_handler_on_shutdown_fn *on_shutdown, void *user_data);
```
