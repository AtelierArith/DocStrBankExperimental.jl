```
constraint_storage_complementarity_mi_traditional_on_off(
    pm::Union{PMD.LPUBFDiagModel,PMD.AbstractUnbalancedNFAModel},
    n::Int,
    i::Int,
    charge_ub::Real,
    discharge_ub::Real
)
```

従来のmld問題の線形ストレージ補完性mi制約

math`sc_{on} + sd_{on} == z_{block}`
