```
metrics(j::LocalQuantumJob, metric_type=TIMESTAMP, statistic="MAX")
```

ジョブ `j` のメトリクスを取得します。メトリクスはジョブスクリプト内の [`log_metric`](@ref) によって生成されます。
