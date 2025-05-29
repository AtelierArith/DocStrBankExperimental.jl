```
ProximalDCGrad
```

A functor `(M,X,p) → ℝ` to represent the gradient of the inner cost function of a [`ManifoldDifferenceOfConvexProximalObjective`](@ref). This is the gradient function of the proximal map cost function of `g`. Based on

$$
    F_{p_k}(p) = \frac{1}{2λ}d_{\mathcal M}(p_k,p)^2 + g(p)
$$

it reads

$$
    \operatorname{grad} F_{p_k}(p) = \operatorname{grad} g(p) - \frac{1}{λ}\log_p p_k
$$

for a point `pk` and a proximal parameter `λ`.

# Fields

  * `grad_g`  - a gradient function
  * `pk` - a point on a manifold
  * `λ`  - the prox parameter

Both interim values can be set using `set_parameter!(::ProximalDCGrad, ::Val{:p}, p)` and `set_parameter!(::ProximalDCGrad, ::Val{:λ}, λ)`, respectively.

# Constructor

```
ProximalDCGrad(grad_g, pk, λ; evaluation=AllocatingEvaluation())
```

Where you specify whether `grad_g` is [`AllocatingEvaluation`](@ref) or [`InplaceEvaluation`](@ref), while this function still always provides *both* signatures.
