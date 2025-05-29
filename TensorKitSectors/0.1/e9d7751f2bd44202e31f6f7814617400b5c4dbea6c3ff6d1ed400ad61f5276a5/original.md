```
struct CU1Irrep <: AbstractIrrep{CU₁}
CU1Irrep(j, s = ifelse(j>zero(j), 2, 0))
Irrep[CU₁](j, s = ifelse(j>zero(j), 2, 0))
```

Represents irreps of the group $U₁ ⋊ C$ ($U₁$ and charge conjugation or reflection), which is also known as just `O₂`. 

## Fields

  * `j::HalfInt`: the value of the $U₁$ charge.
  * `s::Int`: the representation of charge conjugation.

They can take values:

  * if `j == 0`, `s = 0` (trivial charge conjugation) or   `s = 1` (non-trivial charge conjugation)
  * if `j > 0`, `s = 2` (two-dimensional representation)
