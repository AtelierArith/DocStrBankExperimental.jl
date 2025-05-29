```julia
struct InterpSparseHamiltonian{T, dimensionless_time} <: OpenQuantumBase.AbstractHamiltonian{T}
```

補間スパースハミルトニアンオブジェクトを定義します。

# フィールド

  * `interp_obj`: 補間オブジェクト
  * `size`: サイズ
