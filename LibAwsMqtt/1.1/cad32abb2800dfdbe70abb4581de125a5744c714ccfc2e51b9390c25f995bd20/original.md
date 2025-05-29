```
aws_mqtt5_listener_acquire(listener)
```

Adds a reference to an mqtt5 listener.

# Arguments

  * `listener`: listener to add a reference to

# Returns

the listener object

### Prototype

```c
struct aws_mqtt5_listener *aws_mqtt5_listener_acquire(struct aws_mqtt5_listener *listener);
```
