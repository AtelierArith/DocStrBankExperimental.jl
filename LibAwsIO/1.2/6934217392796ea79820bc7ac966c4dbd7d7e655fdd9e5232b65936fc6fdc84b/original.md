```
aws_event_loop_group_release(el_group)
```

Decrements an event loop group's ref count. When the ref count drops to zero, the event loop group will be destroyed.

### Prototype

```c
void aws_event_loop_group_release(struct aws_event_loop_group *el_group);
```
