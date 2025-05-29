```
aws_s3_meta_request_release(meta_request)
```

Release a reference. When the reference count drops to 0, this object will be cleaned up. It's OK to pass in NULL (nothing happens). Always returns NULL.

### Prototype

```c
struct aws_s3_meta_request *aws_s3_meta_request_release(struct aws_s3_meta_request *meta_request);
```
