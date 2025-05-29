```
constraint_storage_complementarity_mi_block_on_off(
    pm::AbstractUnbalancedPowerModel,
    n::Int,
    i::Int,
    charge_ub::Real,
    discharge_ub::Real
)
```

Nonlinear storage complementarity mi constraint for block mld problem.

math``` \begin{align} c^{on}*i * d^{on}*i == z^{bl}*b, i \in {b \in B} \
c^{on}*i c^{ub}*i \geq c*i \
d^{on}*i d^{ub}*i \geq d_i \end{align} ```
