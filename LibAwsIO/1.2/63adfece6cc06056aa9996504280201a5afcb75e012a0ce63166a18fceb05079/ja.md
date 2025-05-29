```
aws_channel_current_clock_time(channel, time_nanos)
```

イベントループのクロックから現在のタイムスタンプをナノ秒単位で取得します。

### プロトタイプ

```c
int aws_channel_current_clock_time(struct aws_channel *channel, uint64_t *time_nanos);
```
