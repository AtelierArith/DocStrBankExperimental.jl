```
ApproximateOctaveBands{LCU,TF} <: AbstractProportionalBands{1,LCU,TF}
```

近似オクターブ比例周波数帯の表現で、`eltype` は `TF` です。

`LCU` パラメータは次の3つの値のいずれかを取ることができます：

  * `:lower`: `struct` は各周波数帯の下端を返します。
  * `:center`: `struct` は各周波数帯の中心を返します。
  * `:upper`: `struct` は各周波数帯の上端を返します。
