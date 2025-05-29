```
aws_mqtt5_listener_release(listener)
```

Removes a reference to an mqtt5 listener. When the reference count drops to zero, the listener's asynchronous destruction will be started.

# Arguments

  * `listener`: listener to remove a reference from

# Returns

NULL

### Prototype

```c
struct aws_mqtt5_listener *aws_mqtt5_listener_release(struct aws_mqtt5_listener *listener);
```
