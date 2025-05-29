```
constraint_mc_storage_block_on_off(
    pm::AbstractUnbalancedPowerModel,
    nw::Int,
    i::Int,
    connections::Vector{Int},
    pmin::Real,
    pmax::Real,
    qmin::Real,
    qmax::Real,
    charge_ub::Real,
    discharge_ub::Real
)
```

block on/off constraint for storage

$$
\begin{align}
\sum_{\substack{c \in \Gamma}} S_{i,c} \geq z^{bl}_b S^{lb}_i, i \in {b \in B} \\
\sum_{\substack{c \in \Gamma}} S_{i,c} \leq z^{bl}_b S^{ub}_i, i \in {b \in B}
\end{align}
$$
