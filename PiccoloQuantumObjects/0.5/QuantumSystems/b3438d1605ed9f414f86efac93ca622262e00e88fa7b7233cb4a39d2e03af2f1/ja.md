```
TimeDependentQuantumSystem <: AbstractQuantumSystem
```

時間依存量子力学の動力学を格納するための構造体です。

# フィールド

  * `H::Function`: 時間を伴うハミルトニアン関数: (a, t) -> H(a, t)。
  * `G::Function`: 時間を伴う同型生成子関数: (a, t) -> G(a, t)。
  * `n_drives::Int`: システム内のドライブの数。
  * `levels::Int`: システム内のレベルの数。
  * `params::Dict{Symbol, Any}`: パラメータの辞書。
