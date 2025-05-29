```
constraint_storage_complementarity_mi_block_on_off(
    pm::AbstractUnbalancedPowerModel,
    n::Int,
    i::Int,
    charge_ub::Real,
    discharge_ub::Real
)
```

ブロック mld 問題のための非線形ストレージ補完性 mi 制約。

math``` \begin{align} c^{on}*i * d^{on}*i == z^{bl}*b, i \in {b \in B} 
c^{on}*i c^{ub}*i \geq c*i 
d^{on}*i d^{ub}*i \geq d_i \end{align} ```
