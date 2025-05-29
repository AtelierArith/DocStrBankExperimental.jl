```
aws_http_message_release(message)
```

Release a hold on the object. The object is deleted when all holds on it are released.

This function always returns NULL so that release-and-assign-NULL can be done with a single statement.

### Prototype

```c
struct aws_http_message *aws_http_message_release(struct aws_http_message *message);
```
