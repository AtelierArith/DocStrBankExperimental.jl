```
aws_s3_request_metrics_get_host_address(metrics, out_host_address)
```

Get the host_address of the request. If unavailable, AWS_ERROR_S3_METRIC_DATA_NOT_AVAILABLE will be raised. If available, out_host_address will be set to a string. Be warned this string's lifetime is tied to the metrics object.

### Prototype

```c
void aws_s3_request_metrics_get_host_address( const struct aws_s3_request_metrics *metrics, const struct aws_string **out_host_address);
```
