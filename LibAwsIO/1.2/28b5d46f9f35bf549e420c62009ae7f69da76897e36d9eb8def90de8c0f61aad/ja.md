```
testing_channel_set_is_on_users_thread(testing, on_users_thread)
```

ハンドラーの「チャネルスレッドパスではない」状態を強制したい場合は、'on*users*thread'をfalseに設定します。それを元に戻したい場合は、再びtrueに設定します。falseに設定した場合は、スケジュールされたタスクを呼び出すために'testing*channel*execute*queued*tasks()'を呼び出す必要があります。

### プロトタイプ

```c
static inline void testing_channel_set_is_on_users_thread(struct testing_channel *testing, bool on_users_thread);
```
