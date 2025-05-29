```
aws_s3_request_metrics_get_operation_name(metrics, out_operation_name)
```

Get the S3 operation name of the request (e.g. "HeadObject"). If unavailable, AWS_ERROR_S3_METRIC_DATA_NOT_AVAILABLE will be raised. If available, out_operation_name will be set to a string. Be warned this string's lifetime is tied to the metrics object.

### Prototype

```c
int aws_s3_request_metrics_get_operation_name( const struct aws_s3_request_metrics *metrics, const struct aws_string **out_operation_name);
```
