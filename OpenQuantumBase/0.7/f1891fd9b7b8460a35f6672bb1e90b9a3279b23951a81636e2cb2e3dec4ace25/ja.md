```julia
struct CustomDenseHamiltonian{T<:Number, dimensionless_time, in_place} <: OpenQuantumBase.AbstractHamiltonian{T<:Number}
```

カスタム関数を持つ時間依存密なハミルトニアンオブジェクトを定義します。

# フィールド

  * `f`: ハミルトニアン `H(s)` のための関数
  * `size`: サイズ
