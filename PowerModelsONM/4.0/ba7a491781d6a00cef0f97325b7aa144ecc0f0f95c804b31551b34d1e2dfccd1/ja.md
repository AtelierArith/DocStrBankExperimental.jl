```
constraint_mc_generator_power_traditional_on_off(pm::AbstractUnbalancedPowerModel, nw::Int, i::Int, connections::Vector{Int}, pmin::Vector{<:Real}, pmax::Vector{<:Real}, qmin::Vector{<:Real}, qmax::Vector{<:Real})
```

発電機の電力に対する一般的な従来型の mld on/off 制約

$$
\begin{align}
S_i \geq z^{gen}_i S^{lb}_i \\
S_i \leq z^{gen}_i S^{ub}_i
\end{align}
$$
