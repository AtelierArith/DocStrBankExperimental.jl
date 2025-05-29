```
aws_s3_client_acquire(client)
```

Add a reference, keeping this object alive. The reference must be released when you are done with it, or it's memory will never be cleaned up. You must not pass in NULL. Always returns the same pointer that was passed in.

### Prototype

```c
struct aws_s3_client *aws_s3_client_acquire(struct aws_s3_client *client);
```
