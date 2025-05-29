```
aws_s3_meta_request_acquire(meta_request)
```

Add a reference, keeping this object alive. The reference must be released when you are done with it, or it's memory will never be cleaned up. You must not pass in NULL. Always returns the same pointer that was passed in.

### Prototype

```c
struct aws_s3_meta_request *aws_s3_meta_request_acquire(struct aws_s3_meta_request *meta_request);
```
