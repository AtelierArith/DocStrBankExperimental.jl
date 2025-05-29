```
DiffFW
```

Callable parametrized wrapper for the Frank-Wolfe algorithm to solve `θ -> argmin_{x ∈ C} f(x, θ)`, which can be differentiated implicitly wrt `θ`.

Reference: [https://arxiv.org/abs/2105.15183](https://arxiv.org/abs/2105.15183) (section 2 + end of appendix A).

# Fields

  * `f`: function `f(x, θ)` to minimize wrt `x`
  * `f_grad1`: gradient `∇ₓf(x, θ)` of `f` wrt `x`
  * `lmo`: linear minimization oracle `θ -> argmin_{x ∈ C} θᵀx` from [FrankWolfe.jl], implicitly defines the convex set `C`
  * `alg`: optimization algorithm from [FrankWolfe.jl](https://github.com/ZIB-IOL/FrankWolfe.jl)
  * `implicit`: implicit function from [ImplicitDifferentiation.jl](https://github.com/gdalle/ImplicitDifferentiation.jl)
