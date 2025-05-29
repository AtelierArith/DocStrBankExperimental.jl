```
transition_matrix(s::AbstractAxisymmetricShape{T, CT}, λ; ...) where {T, CT}
```

Main function for calculating the transition matrix of an axisymmetric shape.

Parameters:

  * `s`: Axisymmetric shape
  * `λ`: Wavelength

Keyword arguments:

  * `threshold`: Convergence threshold, defaults to `0.0001`
  * `ndgs`: Number of discrete Gauss quadrature points per degree, defaults to `4`
  * `routine_generator`: Function that generates the convergence routine, defaults to `routine_mishchenko`
  * `nₛₜₐᵣₜ`: The initial number of the truncation order, defaults to `0`, and the actual value will be calculated automatically using the following formula:

$$
n_{\text{start}} = \max(4, \lceil kr_{\max} + 4.05 \sqrt[3]{kr_{\max}} \rceil)
$$

  * `Ngₛₜₐᵣₜ`: The initial number of discrete Gauss quadrature points, defaults to `nₛₜₐᵣₜ * ndgs`
  * `nₘₐₓ_only`: Only check convergence of `nₘₐₓ`, defaults to `false`, meaning that convergence of both `nₘₐₓ` and `Ng` will be checked
  * `full`: Whether to calculate the whole transition matrix in each iteration, defaults to `false`, and only the `m=m′=0` block will be calculated
  * `reuse`: Whether to reuse the cache of the previous iteration, defaults to `true`
  * `maxiter`: Maximum number of iterations, defaults to `20`
  * `zerofn`: Function that defines the type used for numerical integration, defaults to `() -> zero(CT)` where `CT` is defined by the shape
