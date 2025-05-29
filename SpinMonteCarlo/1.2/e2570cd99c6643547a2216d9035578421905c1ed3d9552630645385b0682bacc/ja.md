```
improved_estimator(model::QuantumXXZ, T::Real, Js::AbstractArray, uf::UnionFind)
```

ループ情報 `uf` を使用して、次の観測量を `Dict{String, Any}` として返します。

# 観測量

  * `"Sign"`

      * 重み関数の符号
  * `"Sign * Energy"`

      * スピン（サイト）あたりのエネルギー
  * `"Sign * Energy^2"`
  * `"Sign * Magnetization"`

      * スピン（サイト）あたりの総磁化 (Sz)
  * `"Sign * |Magnetization|"`
  * `"Sign * Magnetization^2"`
  * `"Sign * Magnetization^4"`
