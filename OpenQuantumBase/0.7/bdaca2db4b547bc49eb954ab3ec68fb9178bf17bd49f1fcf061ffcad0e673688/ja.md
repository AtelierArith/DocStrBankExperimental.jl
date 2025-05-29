```julia
struct InterpDenseHamiltonian{T, isdimensionlesstime} <: OpenQuantumBase.AbstractDenseHamiltonian{T}
```

補間密なハミルトニアンオブジェクトを定義します。

# フィールド

  * `interp_obj`: 補間オブジェクト
  * `size`: サイズ
