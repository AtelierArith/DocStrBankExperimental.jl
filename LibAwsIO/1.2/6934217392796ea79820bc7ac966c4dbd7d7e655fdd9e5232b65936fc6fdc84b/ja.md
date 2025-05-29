```
aws_event_loop_group_release(el_group)
```

イベントループグループの参照カウントを減少させます。参照カウントがゼロになると、イベントループグループは破棄されます。

### プロトタイプ

```c
void aws_event_loop_group_release(struct aws_event_loop_group *el_group);
```
