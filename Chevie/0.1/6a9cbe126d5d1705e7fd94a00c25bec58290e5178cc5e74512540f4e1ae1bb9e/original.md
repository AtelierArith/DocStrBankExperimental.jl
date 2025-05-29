`generic_decomposition_matrix(W,d)`

This  function  obtains  the  `Φ_d`-decomposition  matrix for the reductive group  specified  by  the  Coxeter  group  or  coset  `W`  from the package [GenericDecMats](https://github.com/oscar-system/GenericDecMats.jl).

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

The matrix itself is stored in the field `.scalar` of the returned `struct`.
