```
cyclic_proximal_point!(M, F, proxes, p)
cyclic_proximal_point!(M, mpo, p)
```

perform a cyclic proximal point algorithm in place of `p`.

# Input

  * `M`:      a manifold $\mathcal M$
  * `F`:      a cost function $F:\mathcal M→ℝ$ to minimize
  * `proxes`: an Array of proximal maps (`Function`s) `(M, λ, p) -> q` or `(M, q, λ, p)` for the summands of $F$
  * `p`:      an initial value $p ∈ \mathcal M$

where `f` and the proximal maps `proxes_f` can also be given directly as a [`ManifoldProximalMapObjective`](@ref) `mpo`

for all options, see [`cyclic_proximal_point`](@ref).
