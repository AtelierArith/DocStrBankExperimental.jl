```
ManifoldProximalMapObjective{E<:AbstractEvaluationType, TC, TP, V <: Vector{<:Integer}} <: AbstractManifoldCostObjective{E, TC}
```

specify a problem for solvers based on the evaluation of proximal maps, which represents proximal maps $\operatorname{prox}_{λf_i}$ for summands $f = f_1 + f_2+ … + f_N$ of the cost function $f$.

# Fields

  * `cost`: a function $f:\mathcal M→ℝ$ to minimize
  * `proxes`: proximal maps $\operatorname{prox}_{λf_i}:\mathcal M → \mathcal M$ as functions `(M, λ, p) -> q` or in-place `(M, q, λ, p)`.
  * `number_of_proxes`: number of proximal maps per function, to specify when one of the maps is a combined one such that the proximal maps functions return more than one entry per function, you have to adapt this value. if not specified, it is set to one prox per function.

# Constructor

```
ManifoldProximalMapObjective(f, proxes_f::Union{Tuple,AbstractVector}, numer_of_proxes=onex(length(proxes));
   evaluation=Allocating)
```

Generate a proximal problem with a tuple or vector of funtions, where by default every function computes a single prox of one component of $f$.

```
ManifoldProximalMapObjective(f, prox_f); evaluation=Allocating)
```

Generate a proximal objective for $f$ and its proxial map $\operatorname{prox}_{λf}$

# See also

[`cyclic_proximal_point`](@ref), [`get_cost`](@ref), [`get_proximal_map`](@ref)
