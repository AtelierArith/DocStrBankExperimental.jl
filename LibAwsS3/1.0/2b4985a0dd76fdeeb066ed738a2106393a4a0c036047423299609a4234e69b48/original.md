```
aws_s3_request_metrics_get_request_path_query(metrics, out_request_path_query)
```

Get the path and query of the request. If unavailable, AWS_ERROR_S3_METRIC_DATA_NOT_AVAILABLE will be raised. If available, out_request_path_query will be set to a string. Be warned this string's lifetime is tied to the metrics object.

### Prototype

```c
void aws_s3_request_metrics_get_request_path_query( const struct aws_s3_request_metrics *metrics, const struct aws_string **out_request_path_query);
```
