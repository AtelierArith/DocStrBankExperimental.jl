```
LinearizedDCCost
```

A functor `(M,q) → ℝ` to represent the inner problem of a [`ManifoldDifferenceOfConvexObjective`](@ref). This is a cost function of the form

$$
    F_{p_k,X_k}(p) = g(p) - ⟨X_k, \log_{p_k}p⟩
$$

for a point `p_k` and a tangent vector `X_k` at `p_k` (for example outer iterates) that are stored within this functor as well.

# Fields

  * `g` a function
  * `pk` a point on a manifold
  * `Xk` a tangent vector at `pk`

Both interim values can be set using `set_manopt_parameter!(::LinearizedDCCost, ::Val{:p}, p)` and `set_manopt_parameter!(::LinearizedDCCost, ::Val{:X}, X)`, respectively.

# Constructor

```
LinearizedDCCost(g, p, X)
```
