```
aws_event_loop_thread_is_callers_thread(event_loop)
```

Returns true if the event loop's thread is the same thread that called this function, otherwise false.

### Prototype

```c
bool aws_event_loop_thread_is_callers_thread(struct aws_event_loop *event_loop);
```
