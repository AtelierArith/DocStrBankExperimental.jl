```
aws_event_loop_thread_is_callers_thread(event_loop)
```

この関数を呼び出したスレッドがイベントループのスレッドと同じであればtrueを返し、そうでなければfalseを返します。

### プロトタイプ

```c
bool aws_event_loop_thread_is_callers_thread(struct aws_event_loop *event_loop);
```
