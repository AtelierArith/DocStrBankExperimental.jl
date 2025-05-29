```julia
struct AdiabaticFrameHamiltonian{T} <: OpenQuantumBase.AbstractDenseHamiltonian{T}
```

アディアバティックフレームにおける時間依存ハミルトニアンを定義します。

# フィールド

  * `geometric`: 幾何学的部分
  * `diagonal`: アディアバティック部分
  * `size`: ハミルトニアンのサイズ
