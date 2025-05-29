```
aws_s3_request_metrics_get_request_id(metrics, out_request_id)
```

*********************************** Getters for s3 request metrics ***********************************************

Get the request ID from [`aws_s3_request_metrics`](@ref). If unavailable, AWS_ERROR_S3_METRIC_DATA_NOT_AVAILABLE will be raised. If available, out_request_id will be set to a string. Be warned this string's lifetime is tied to the metrics object.

### Prototype

```c
int aws_s3_request_metrics_get_request_id( const struct aws_s3_request_metrics *metrics, const struct aws_string **out_request_id);
```
