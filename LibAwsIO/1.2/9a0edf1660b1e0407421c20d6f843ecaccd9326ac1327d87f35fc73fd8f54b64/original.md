```
aws_event_loop_get_impl(event_loop)
```

```c++
 - Don't use outside of testing.

 Returns the opaque internal user data of an event loop.  Can be cast into a specific implementation by
 privileged consumers.
 

```

### Prototype

```c
void *aws_event_loop_get_impl(struct aws_event_loop *event_loop);
```
