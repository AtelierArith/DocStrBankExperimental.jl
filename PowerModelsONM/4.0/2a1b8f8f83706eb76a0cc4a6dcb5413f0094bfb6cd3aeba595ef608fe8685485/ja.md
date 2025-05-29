```
constraint_mc_storage_traditional_on_off(
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

ストレージのための従来のオン/オフ制約

$$
\begin{align}
\sum_{\substack{c \in \Gamma}} S_{i,c} \geq z^{strg}_i S^{lb}_i \\
\sum_{\substack{c \in \Gamma}} S_{i,c} \leq z^{strg}_i S^{ub}_i
\end{align}
$$
