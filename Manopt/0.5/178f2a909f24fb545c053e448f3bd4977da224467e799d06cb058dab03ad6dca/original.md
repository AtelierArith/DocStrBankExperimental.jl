```
LinearizedDCGrad
```

A functor `(M,X,p) → ℝ` to represent the gradient of the inner problem of a [`ManifoldDifferenceOfConvexObjective`](@ref). This is a gradient function of the form

$$
    F_{p_k,X_k}(p) = g(p) - ⟨X_k, \log_{p_k}p⟩
$$

its gradient is given by using $F=F_1(F_2(p))$, where $F_1(X) = ⟨X_k,X⟩$ and $F_2(p) = \log_{p_k}p$ and the chain rule as well as the adjoint differential of the logarithmic map with respect to its argument for $D^*F_2(p)$

$$
    \operatorname{grad} F(q) = \operatorname{grad} f(q) - DF_2^*(q)[X]
$$

for a point `pk` and a tangent vector `Xk` at `pk` (the outer iterates) that are stored within this functor as well

# Fields

  * `grad_g!!` the gradient of $g$ (see also [`LinearizedDCCost`](@ref))
  * `pk` a point on a manifold
  * `Xk` a tangent vector at `pk`

Both interim values can be set using `set_parameter!(::LinearizedDCGrad, ::Val{:p}, p)` and `set_parameter!(::LinearizedDCGrad, ::Val{:X}, X)`, respectively.

# Constructor

```
LinearizedDCGrad(grad_g, p, X; evaluation=AllocatingEvaluation())
```

Where you specify whether `grad_g` is [`AllocatingEvaluation`](@ref) or [`InplaceEvaluation`](@ref), while this function still provides *both* signatures.
