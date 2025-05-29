```
admm(x0, prox_f!, prox_g!; λ=1., α=1., ϵ_abs=1e-7, ϵ_rel=1e-4, max_iter=1000)
```

Minimize an objective function $f(x) + g(x)$, where $f(x)$ and $g(x)$ can both be nonsmooth, using alternating direction method of multipliers, also known as Douglas-Rachford splitting. The alternating direction method of multipliers method has two hyperparameters, `λ` and `α`. `λ` controls the scaling of the update steps, i.e. a pseudo step size, and is equal to the inverse of the augmented Lagrangian parameter. $α ∈ [0,2]$ is the relaxation parameter, where $α < 1$ denotes under-relaxation and $α > 1$ over-relaxation.

#### Arguments

  * `x0::AbstractVector`: initial parameter values (n x 1)
  * `prox_f!::Function` : proximal operator of $f(x)$
  * `prox_g!::Function` : proximal operator of $g(x)$
  * `λ::Real`           : proximal scaling parameter
  * `α::Real`           : relaxation parameter
  * `ϵ_abs::Real`       : absolute tolerance
  * `ϵ_rel::Real`       : relative tolerance
  * `max_iter::Integer` : max number of iterations

#### Returns

  * `x::AbstractVector` : minimizer $∈ dom f$ (n x 1)
  * `z::AbstractVector` : minimizer $∈ dom g$ (n x 1)
