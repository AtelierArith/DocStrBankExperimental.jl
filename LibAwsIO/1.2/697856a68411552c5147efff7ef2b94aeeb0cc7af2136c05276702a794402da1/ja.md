```
aws_event_loop_group_get_loop_at(el_group, index)
```

特定のインデックスにあるイベントループを返します。インデックスが範囲外の場合、nullが返されます。

### プロトタイプ

```c
struct aws_event_loop *aws_event_loop_group_get_loop_at(struct aws_event_loop_group *el_group, size_t index);
```
