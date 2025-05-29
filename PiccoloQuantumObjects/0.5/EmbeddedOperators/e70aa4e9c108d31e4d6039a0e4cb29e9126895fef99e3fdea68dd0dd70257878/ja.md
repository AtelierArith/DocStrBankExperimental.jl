```
EmbeddedOperator
```

埋め込まれた演算子型は、より大きな量子システムの部分空間に埋め込まれた演算子を表します。

# フィールド

  * `operator::Matrix{ComplexF64}`: サイズ `prod(subsystem_levels) x prod(subsystem_levels)` の埋め込まれた演算子。
  * `subspace::Vector{Int}`: 演算子が埋め込まれている部分空間のインデックス。
  * `subsystem_levels::Vector{Int}`: 複合システム内のサブシステムのレベル。
