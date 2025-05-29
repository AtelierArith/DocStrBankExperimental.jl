```
aws_http2_stream_manager_fetch_metrics(http2_stream_manager, out_metrics)
```

Fetch the current metrics from stream manager.

# Arguments

  * `http2_stream_manager`:
  * `out_metrics`: The metrics to be fetched

### Prototype

```c
void aws_http2_stream_manager_fetch_metrics( const struct aws_http2_stream_manager *http2_stream_manager, struct aws_http_manager_metrics *out_metrics);
```
