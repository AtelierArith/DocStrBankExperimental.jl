`InducedDecompositionMatrix(R,W,d)`

は、Levi `L` から冗長群 `W` への、一般的な `Φ_d` 分解行列の誘導を返します。

```julia-repl
julia> W=rootdatum(:psu,6)
psu₆

julia> L=reflection_subgroup(W,[1,2,4,5])
psu₆₍₁₂₄₅₎=(A₂A₂)₍₁₂₄₃₎Φ₁

julia> InducedDecompositionMatrix(L,W,6)
Induced Φ₆-decomposition matrix from psu₆₍₁₂₄₅₎=(A₂A₂)₍₁₂₄₃₎Φ₁ to psu₆

┌────┬────────┐
│    │ps ps A₂│
├────┼────────┤
│²A₅ │ .  .  .│
│.3  │ 1  .  .│
│3.  │ 1  .  .│
│.21 │ 1  1  .│
│1.2 │ 2  1  .│
│21. │ 1  1  .│
│2.1 │ 2  1  .│
│.111│ .  1  1│
│111.│ .  1  1│
│1.11│ 1  2  1│
│11.1│ 1  2  1│
└────┴────────┘
```

行列自体は、返された `struct` のフィールド `.scalar` に格納されています。
