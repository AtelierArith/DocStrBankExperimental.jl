```
scatter_array(sym, x::Array, workers; dim=1)::Dinfo
```

次元 `dim` に沿って `workers` に分散させた配列 `x` のほぼ等しい部分を、ワーカー固有の変数 `sym` に分配します。

分散データのための `Dinfo` 構造体を返します。
