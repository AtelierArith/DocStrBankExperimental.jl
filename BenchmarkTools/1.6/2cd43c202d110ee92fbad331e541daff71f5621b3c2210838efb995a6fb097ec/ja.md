```
tune!(group::BenchmarkGroup; verbose::Bool = false, pad = "", kwargs...)
```

`BenchmarkGroup` インスタンスを調整します。ほとんどのベンチマークでは、`tune!` は特定のベンチマークに対して適切なパラメータを決定するために多くの評価を行う必要があります - 実際、試行を実行する際に行われる評価よりも多くの評価が必要です。実際、総ベンチマーク時間の大部分は、実際に試行を実行するのではなく、パラメータの調整に費やされることが通常です。
