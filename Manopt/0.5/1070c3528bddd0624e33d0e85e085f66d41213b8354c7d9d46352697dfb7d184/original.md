```
ProximalDCCost
```

A functor `(M, p) → ℝ` to represent the inner cost function of a [`ManifoldDifferenceOfConvexProximalObjective`](@ref). This is the cost function of the proximal map of `g`.

$$
    F_{p_k}(p) = \frac{1}{2λ}d_{\mathcal M}(p_k,p)^2 + g(p)
$$

for a point `pk` and a proximal parameter $λ$.

# Fields

  * `g`  - a function
  * `pk` - a point on a manifold
  * `λ`  - the prox parameter

Both interim values can be set using `set_parameter!(::ProximalDCCost, ::Val{:p}, p)` and `set_parameter!(::ProximalDCCost, ::Val{:λ}, λ)`, respectively.

# Constructor

```
ProximalDCCost(g, p, λ)
```
