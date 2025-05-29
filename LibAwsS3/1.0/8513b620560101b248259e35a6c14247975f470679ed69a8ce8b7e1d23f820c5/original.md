```
aws_s3_request_metrics_acquire(metrics)
```

Add a reference, keeping this object alive. The reference must be released when you are done with it, or it's memory will never be cleaned up. Always returns the same pointer that was passed in.

### Prototype

```c
struct aws_s3_request_metrics *aws_s3_request_metrics_acquire(struct aws_s3_request_metrics *metrics);
```
