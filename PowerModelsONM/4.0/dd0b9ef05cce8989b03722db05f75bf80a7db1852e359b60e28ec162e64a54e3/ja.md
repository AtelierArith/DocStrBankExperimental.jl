```
constraint_mc_generator_power_block_on_off(
    pm::AbstractUnbalancedPowerModel,
    nw::Int,
    i::Int,
    connections::Vector{Int},
    pmin::Vector{<:Real},
    pmax::Vector{<:Real},
    qmin::Vector{<:Real},
    qmax::Vector{<:Real}
)
```

発電機の電力に対する一般的なブロック mld on/off 制約

$$
\begin{align}
S_i \geq z^{bl}_b S^{lb}_i, i \in {b \in B} \\
S_i \leq z^{bl}_b S^{ub}_i, i \in {b \in B}
\end{align}
$$
