```
subgradient_method!(M, f, ∂f, p)
subgradient_method!(M, sgo, p)
```

perform a subgradient method $p_{k+1} = \mathrm{retr}(p_k, s_k∂f(p_k))$,

# Input

  * `M`:  a manifold $\mathcal M$
  * `f`:  a cost function $f:\mathcal M→ℝ$ to minimize
  * `∂f`: the (sub)gradient $∂f: \mathcal M→ T\mathcal M$ of F restricted to always only returning one value/element from the subdifferential. This function can be passed as an allocation function `(M, p) -> X` or a mutating function `(M, X, p) -> X`, see `evaluation`.
  * `p`:  an initial value $p_0=p ∈ \mathcal M$

alternatively to `f` and `∂f` a [`ManifoldSubgradientObjective`](@ref) `sgo` can be provided.

for more details and all optional parameters, see [`subgradient_method`](@ref).
