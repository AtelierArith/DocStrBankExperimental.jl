```
AbstractProportionalBands{NO,LCU,TF} <: AbstractVector{TF}
```

バンド分数 `NO` と `eltype` `TF` を持つ正確な比例周波数バンドを表す抽象型です。

`LCU` パラメータは次の3つの値のいずれかを取ることができます：

  * `:lower`: `struct` は各周波数バンドの下端を返します。
  * `:center`: `struct` は各周波数バンドの中心を返します。
  * `:upper`: `struct` は各周波数バンドの上端を返します。
