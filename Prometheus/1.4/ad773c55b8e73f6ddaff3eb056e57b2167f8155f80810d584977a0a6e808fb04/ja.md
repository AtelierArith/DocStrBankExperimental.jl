```
Prometheus.inc(counter::Counter, v::Real = 1)
```

カウンターの値を `v` で増加させます。値のデフォルトは `v = 1` です。

`v < 0` の場合は `Prometheus.ArgumentError` をスローします（カウンターは減少してはいけません）。
