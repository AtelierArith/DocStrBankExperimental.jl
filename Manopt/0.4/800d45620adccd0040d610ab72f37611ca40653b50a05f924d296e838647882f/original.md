```
ManifoldProximalMapObjective{E<:AbstractEvaluationType, TC, TP, V <: Vector{<:Integer}} <: AbstractManifoldCostObjective{E, TC}
```

specify a problem for solvers based on the evaluation of proximal maps.

# Fields

  * `cost` - a function $F:\mathcal M→ℝ$ to minimize
  * `proxes` - proximal maps $\operatorname{prox}_{λ\varphi}:\mathcal M→\mathcal M$ as functions `(M, λ, p) -> q`.
  * `number_of_proxes` - (`ones(length(proxes))`` number of proximal maps per function, to specify when one of the maps is a combined one such that the proximal maps functions return more than one entry per function, you have to adapt this value. if not specified, it is set to one prox per function.

# See also

[`cyclic_proximal_point`](@ref), [`get_cost`](@ref), [`get_proximal_map`](@ref)
