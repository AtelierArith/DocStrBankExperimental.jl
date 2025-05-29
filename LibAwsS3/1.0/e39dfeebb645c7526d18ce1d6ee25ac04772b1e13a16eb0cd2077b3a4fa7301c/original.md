```
aws_s3_request_metrics_get_ip_address(metrics, out_ip_address)
```

Get the IP address of the request connected to. If unavailable, AWS_ERROR_S3_METRIC_DATA_NOT_AVAILABLE will be raised. If available, out_ip_address will be set to a string. Be warned this string's lifetime is tied to the metrics object.

### Prototype

```c
int aws_s3_request_metrics_get_ip_address( const struct aws_s3_request_metrics *metrics, const struct aws_string **out_ip_address);
```
