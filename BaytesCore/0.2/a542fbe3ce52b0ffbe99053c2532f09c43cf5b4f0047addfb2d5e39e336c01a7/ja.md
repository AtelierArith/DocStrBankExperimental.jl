```julia
struct ArrayConfig{K, T<:BaytesCore.DataSorting}
```

配列設定構造体。

データが行または列方向に伝播されるかどうかをチェックします。

# フィールド

  * `size::NTuple{K, Int64} where K`: データの次元。
  * `sorted::BaytesCore.DataSorting`: データが行によってソートされているかどうかのブール値。
