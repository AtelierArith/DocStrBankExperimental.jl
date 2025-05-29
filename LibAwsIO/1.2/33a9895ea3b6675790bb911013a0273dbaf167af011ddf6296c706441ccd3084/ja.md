```
aws_event_loop_group_acquire(el_group)
```

イベントループグループの参照カウントを増加させ、呼び出し元がそれを参照できるようにします。

渡されたのと同じイベントループグループを返します。

### プロトタイプ

```c
struct aws_event_loop_group *aws_event_loop_group_acquire(struct aws_event_loop_group *el_group);
```
