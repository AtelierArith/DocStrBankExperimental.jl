```
constraint_storage_complementarity_mi_traditional_on_off(
    pm::Union{PMD.LPUBFDiagModel,PMD.AbstractUnbalancedNFAModel},
    n::Int,
    i::Int,
    charge_ub::Real,
    discharge_ub::Real
)
```

linear storage complementarity mi constraint for traditional mld problem

math`sc_{on} + sd_{on} == z_{block}`
