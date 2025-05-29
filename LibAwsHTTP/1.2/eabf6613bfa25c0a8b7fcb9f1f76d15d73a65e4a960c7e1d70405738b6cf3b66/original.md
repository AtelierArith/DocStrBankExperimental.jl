```
aws_http_message_acquire(message)
```

Acquire a hold on the object, preventing it from being deleted until [`aws_http_message_release`](@ref)() is called by all those with a hold on it.

This function returns the passed in message (possibly NULL) so that acquire-and-assign can be done with a single statement.

### Prototype

```c
struct aws_http_message *aws_http_message_acquire(struct aws_http_message *message);
```
