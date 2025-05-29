```
testing_channel_complete_written_messages_immediately(testing, complete_immediately, complete_error_code)
```

書き込まれたメッセージが即座に on*complete コールバックを呼び出すかどうかを設定します。on*complete コールバックは呼び出された後にクリアされます。

### プロトタイプ

```c
static inline void testing_channel_complete_written_messages_immediately( struct testing_channel *testing, bool complete_immediately, int complete_error_code);
```
