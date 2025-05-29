```
aws_channel_thread_is_callers_thread(channel)
```

呼び出し元がイベントループのスレッド上にいる場合はtrueを返します。falseの場合、aws*channel*schedule_task()を使用する必要があります。この関数は、任意のスレッドから呼び出すことが安全です。

### プロトタイプ

```c
bool aws_channel_thread_is_callers_thread(struct aws_channel *channel);
```
