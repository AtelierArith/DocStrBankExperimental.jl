```
struct SU2Irrep <: AbstractIrrep{SU₂}
SU2Irrep(j::Real)
Irrep[SU₂](j::Real)
```

Represents irreps of the group $SU₂$. The irrep is labelled by a half integer `j` which can be entered as an abitrary `Real`, but is stored as a `HalfInt` from the HalfIntegers.jl package.

## Fields

  * `j::HalfInt`: the label of the irrep, which can be any non-negative half integer.
