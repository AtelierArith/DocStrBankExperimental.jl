```
aws_event_loop_group_acquire(el_group)
```

Increments the reference count on the event loop group, allowing the caller to take a reference to it.

Returns the same event loop group passed in.

### Prototype

```c
struct aws_event_loop_group *aws_event_loop_group_acquire(struct aws_event_loop_group *el_group);
```
