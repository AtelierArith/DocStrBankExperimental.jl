```julia
struct ConstantCouplings <: OpenQuantumBase.AbstractCouplings
```

定常系バス結合演算子を定義します。

# フィールド

  * `mats`: 独立した結合演算子のための1次元配列
  * `str_rep`: 結合の文字列表現（表示目的のため）
