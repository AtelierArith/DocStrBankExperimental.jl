```julia
struct CustomCouplings <: OpenQuantumBase.AbstractTimeDependentCouplings
```

`CustomCouplings` は、ユーザー定義の結合演算子のためのコンテナです。

# フィールド

  * `coupling`: 結合行列を返す呼び出し可能なオブジェクトの1次元配列
  * `size`: 結合演算子のサイズ
