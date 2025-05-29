`generic_decomposition_matrix(W,d)`

この関数は、パッケージ [GenericDecMats](https://github.com/oscar-system/GenericDecMats.jl) によって指定されたコクセター群またはコセット `W` に対する冗長群の `Φ_d`-分解行列を取得します。

```julia-repl
julia> W=rootdatum(:psu,5)
psu₅
```

```julia-rep1
julia> generic_decomposition_matrix(W,13)
!!! Φ-decomposition matrices available for ²A₄: Φ₁₀ Φ₂ Φ₄ Φ₆
```

```julia-repl
julia> generic_decomposition_matrix(W,10)
Φ₁₀-decomposition matrix for psu₅
┌──────┬─────────────────────────┐
│      │ps 21 ps ps ps 2111 11111│
├──────┼─────────────────────────┤
│2.    │ 1  .  .  .  .    .     .│
│²A₂:2 │ .  1  .  .  .    .     .│
│11.   │ .  .  1  .  .    .     .│
│1.1   │ 1  .  .  1  .    .     .│
│.2    │ .  .  .  .  1    .     .│
│²A₂:11│ .  1  .  .  .    1     .│
│.11   │ .  .  .  1  .    .     1│
└──────┴─────────────────────────┘
```

行列自体は、返された `struct` のフィールド `.scalar` に格納されています。
