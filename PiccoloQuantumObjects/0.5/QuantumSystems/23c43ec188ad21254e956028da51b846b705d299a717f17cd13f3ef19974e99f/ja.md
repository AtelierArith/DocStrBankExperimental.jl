```
QuantumSystem <: AbstractQuantumSystem
```

量子力学的な動態を格納するための構造体です。

# フィールド

  * `H::Function`: 減衰を除くハミルトニアン関数: a -> H(a)。
  * `G::Function`: 減衰を含む同型生成子関数: a -> G(a)。
  * `levels::Int`: システム内のレベルの数。
  * `n_drives::Int`: システム内のドライブの数。
