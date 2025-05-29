```
aws_event_loop_current_clock_time(event_loop, time_nanos)
```

イベントループのクロックの現在のタイムスタンプをナノ秒単位で取得します。この関数はスレッドセーフです。

### プロトタイプ

```c
int aws_event_loop_current_clock_time(const struct aws_event_loop *event_loop, uint64_t *time_nanos);
```
