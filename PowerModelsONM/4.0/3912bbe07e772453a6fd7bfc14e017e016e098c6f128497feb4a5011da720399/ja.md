```
constraint_storage_complementarity_mi_block_on_off(pm::Union{PMD.LPUBFDiagModel,PMD.AbstractUnbalancedNFAModel}, n::Int, i::Int, charge_ub::Real, discharge_ub::Real)
```

ブロック MLD 問題のための線形ストレージ補完性 MI 制約

math`sc_{on} + sd_{on} == z_{block}`
