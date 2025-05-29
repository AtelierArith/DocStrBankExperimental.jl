```
struct U1Irrep <: AbstractIrrep{U₁}
U1Irrep(charge::Real)
Irrep[U₁](charge::Real)
```

Represents irreps of the group $U₁$. The irrep is labelled by a charge, which should be an integer for a linear representation. However, it is often useful to allow half integers to represent irreps of $U₁$ subgroups of $SU₂$, such as the Sz of spin-1/2 system. Hence, the charge is stored as a `HalfInt` from the package HalfIntegers.jl, but can be entered as arbitrary `Real`. The sequence of the charges is: 0, 1/2, -1/2, 1, -1, ...

## Fields

  * `charge::HalfInt`: the label of the irrep, which can be any half integer.
