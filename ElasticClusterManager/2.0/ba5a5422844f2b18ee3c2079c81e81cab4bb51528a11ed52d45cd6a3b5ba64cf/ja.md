```
ElasticClusterManager.elastic_worker(
    cookie::AbstractString, addr::AbstractString="127.0.0.1", port::Integer = 9009;
    forward_stdout::Bool = true,
    Base.@nospecialize(env::AbstractVector = [],)
)
```

IPアドレス `addr` とポート `port` でメインのJuliaプロセスに接続する弾力的なワーカープロセスを開始します。

戻り値はありません。
