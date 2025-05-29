```
convex_bundle_method!(M, f, ∂f, p)
```

perform a bundle method $p_{j+1} = \mathrm{retr}(p_k, -g_k)$ in place of `p`.

# Input

  * `M`:  a manifold $\mathcal M$
  * `f`:  a cost function $f:\mathcal M→ℝ$ to minimize
  * `∂f`: the (sub)gradient $∂f:\mathcal M→ T\mathcal M$ of F restricted to always only returning one value/element from the subdifferential. This function can be passed as an allocation function `(M, p) -> X` or a mutating function `(M, X, p) -> X`, see `evaluation`.
  * `p`:  an initial value $p_0=p ∈ \mathcal M$

for more details and all optional parameters, see [`convex_bundle_method`](@ref).
