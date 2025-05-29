```
aws_http2_stream_manager_fetch_metrics(http2_stream_manager, out_metrics)
```

ストリームマネージャから現在のメトリクスを取得します。

# 引数

  * `http2_stream_manager`:
  * `out_metrics`: 取得するメトリクス

### プロトタイプ

```c
void aws_http2_stream_manager_fetch_metrics( const struct aws_http2_stream_manager *http2_stream_manager, struct aws_http_manager_metrics *out_metrics);
```
