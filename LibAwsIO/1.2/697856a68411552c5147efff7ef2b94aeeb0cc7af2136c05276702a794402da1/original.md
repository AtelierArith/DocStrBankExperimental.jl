```
aws_event_loop_group_get_loop_at(el_group, index)
```

Returns the event loop at a particular index. If the index is out of bounds, null is returned.

### Prototype

```c
struct aws_event_loop *aws_event_loop_group_get_loop_at(struct aws_event_loop_group *el_group, size_t index);
```
