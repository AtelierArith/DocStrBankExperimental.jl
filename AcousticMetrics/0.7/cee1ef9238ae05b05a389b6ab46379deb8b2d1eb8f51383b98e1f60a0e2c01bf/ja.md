```
ExactProportionalBands{NO,LCU,TF} <: AbstractProportionalBands{NO,LCU,TF}
```

バンド分数 `NO` と `eltype` `TF` を持つ正確な比例周波数バンドの表現。

`LCU` パラメータは次の3つの値のいずれかを取ることができます：

  * `:lower`: `struct` は各周波数バンドの下限を返します。
  * `:center`: `struct` は各周波数バンドの中心を返します。
  * `:upper`: `struct` は各周波数バンドの上限を返します。
