```
constraint_storage_complementarity_mi_block_on_off(pm::Union{PMD.LPUBFDiagModel,PMD.AbstractUnbalancedNFAModel}, n::Int, i::Int, charge_ub::Real, discharge_ub::Real)
```

linear storage complementarity mi constraint for block mld problem

math`sc_{on} + sd_{on} == z_{block}`
