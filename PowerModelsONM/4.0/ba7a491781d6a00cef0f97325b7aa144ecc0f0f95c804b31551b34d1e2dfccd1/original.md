```
constraint_mc_generator_power_traditional_on_off(pm::AbstractUnbalancedPowerModel, nw::Int, i::Int, connections::Vector{Int}, pmin::Vector{<:Real}, pmax::Vector{<:Real}, qmin::Vector{<:Real}, qmax::Vector{<:Real})
```

Generic traditional mld on/off constraint for generator power

$$
\begin{align}
S_i \geq z^{gen}_i S^{lb}_i \\
S_i \leq z^{gen}_i S^{ub}_i
\end{align}
$$
