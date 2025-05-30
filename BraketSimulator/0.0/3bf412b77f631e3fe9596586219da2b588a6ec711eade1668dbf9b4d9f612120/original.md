```
evolve!(dms::DensityMatrixSimulator{T, S<:AbstractMatrix{T}}, operations::Vector{Instruction}) -> DensityMatrixSimulator{T, S}
```

Apply each operation of `operations` in-place to the density matrix contained in `dms`.

Effectively, perform the operation:

$\hat{\rho} \to \hat{A}^\dag \hat{\rho} \hat{A}$

for each operation $\hat{A}$ in `operations`.
