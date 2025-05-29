```
aws_http_message_get_response_status(response_message, out_status_code)
```

Get the status code (response messages only). If no status is set, AWS_ERROR_HTTP_DATA_NOT_AVAILABLE is raised.

### Prototype

```c
int aws_http_message_get_response_status(const struct aws_http_message *response_message, int *out_status_code);
```
