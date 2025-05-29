```
aws_s3_request_metrics_release(metrics)
```

Release a reference. When the reference count drops to 0, this object will be cleaned up. It's OK to pass in NULL (nothing happens). Always returns NULL.

### Prototype

```c
struct aws_s3_request_metrics *aws_s3_request_metrics_release(struct aws_s3_request_metrics *metrics);
```
