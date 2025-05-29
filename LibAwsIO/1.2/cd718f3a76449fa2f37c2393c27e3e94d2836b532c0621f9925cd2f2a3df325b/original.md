```
aws_event_loop_complete_destroy(event_loop)
```

```c++

 Waits for an event loop to complete its destruction process.  aws_event_loop_start_destroy() must have been called
 previously for this function to not deadlock.
 

```

### Prototype

```c
void aws_event_loop_complete_destroy(struct aws_event_loop *event_loop);
```
