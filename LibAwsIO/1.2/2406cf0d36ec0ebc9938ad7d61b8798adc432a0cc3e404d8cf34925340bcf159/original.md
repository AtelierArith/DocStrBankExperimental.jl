```
aws_event_loop_group_get_next_loop(el_group)
```

Fetches the next loop for use. The purpose is to enable load balancing across loops. You should not depend on how this load balancing is done as it is subject to change in the future. Currently it uses the "best-of-two" algorithm based on the load factor of each loop.

### Prototype

```c
struct aws_event_loop *aws_event_loop_group_get_next_loop(struct aws_event_loop_group *el_group);
```
