```
aws_event_loop_start_destroy(event_loop)
```

```c++

 Signals an event loop to begin its destruction process.  If an event loop's implementation of this API does anything,
 it must be quick and non-blocking.  Most event loop implementations have an empty implementation for this function.
 

```

### Prototype

```c
void aws_event_loop_start_destroy(struct aws_event_loop *event_loop);
```
