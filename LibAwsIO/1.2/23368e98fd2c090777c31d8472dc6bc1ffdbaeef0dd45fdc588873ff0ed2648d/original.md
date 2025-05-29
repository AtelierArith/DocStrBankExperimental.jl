```
aws_event_loop_clean_up_base(event_loop)
```

```c++
 - Don't use outside of testing.

 Common cleanup code for all implementations.
 This is only called from the *destroy() function of event loop implementations.
 

```

### Prototype

```c
void aws_event_loop_clean_up_base(struct aws_event_loop *event_loop);
```
