```
struct ZNIrrep{N} <: AbstractIrrep{ℤ{N}}
ZNIrrep{N}(n::Integer)
Irrep[ℤ{N}](n::Integer)
```

Represents irreps of the group $ℤ_N$ for some value of `N<64`. (We need 2*(N-1) <= 127 in order for a ⊗ b to work correctly.) For `N` equals `2`, `3` or `4`, `ℤ{N}` can be replaced by `ℤ₂`, `ℤ₃`, `ℤ₄`. An arbitrary `Integer` `n` can be provided to the constructor, but only the value `mod(n, N)` is relevant.

## Fields

  * `n::Int8`: the integer label of the irrep, modulo `N`.
