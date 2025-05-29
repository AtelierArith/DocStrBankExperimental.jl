```
aws_event_loop_destroy(event_loop)
```

```c++
 - Don't use outside of testing.

 Destroys an event loop implementation.
 If the event loop is still in a running state, this function will block waiting on the event loop to shutdown.
 If the event loop is shared by multiple threads then destroy must be called by exactly one thread. All other threads
 must ensure their API calls to the event loop happen-before the call to destroy.

 Internally, this calls aws_event_loop_start_destroy() followed by aws_event_loop_complete_destroy()
 

```

### Prototype

```c
void aws_event_loop_destroy(struct aws_event_loop *event_loop);
```
