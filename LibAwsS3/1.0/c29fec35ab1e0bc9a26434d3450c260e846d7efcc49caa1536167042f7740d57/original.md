```
aws_s3_client_release(client)
```

Release a reference. When the reference count drops to 0, this object will be cleaned up. It's OK to pass in NULL (nothing happens). Always returns NULL.

### Prototype

```c
struct aws_s3_client *aws_s3_client_release(struct aws_s3_client *client);
```
