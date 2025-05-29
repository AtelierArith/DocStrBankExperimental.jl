```
aws_http_connection_manager_fetch_metrics(manager, out_metrics)
```

接続マネージャから現在のマネージャメトリクスを取得します。

### プロトタイプ

```c
void aws_http_connection_manager_fetch_metrics( const struct aws_http_connection_manager *manager, struct aws_http_manager_metrics *out_metrics);
```
