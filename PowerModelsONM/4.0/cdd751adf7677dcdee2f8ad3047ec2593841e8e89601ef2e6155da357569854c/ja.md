```
constraint_storage_complementarity_mi_traditional_on_off(
    pm::AbstractUnbalancedPowerModel,
    n::Int,
    i::Int,
    charge_ub::Real,
    discharge_ub::Real
)
```

従来のmld問題に対する非線形ストレージ補完性mi制約。

math``` \begin{align} c^{on}*i d^{on}*i = z^{strg}*i 
c^{on}*i c^{ub}*i \geq c*i 
d^{on}*i d^{ub}*i \geq d_i \end{align} ```
