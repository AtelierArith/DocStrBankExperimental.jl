```
metrics(j::AwsQuantumJob; metric_type="timestamp", statistic="max")
```

ジョブ `j` のメトリクスを取得します。メトリクスはジョブスクリプト内の [`log_metric`](@ref) によって生成されます。
