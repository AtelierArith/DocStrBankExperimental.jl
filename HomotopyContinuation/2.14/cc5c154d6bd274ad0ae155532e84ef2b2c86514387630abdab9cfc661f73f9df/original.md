```
newton(
    F::AbstractSystem,
    x₀::AbstractVector,
    p = nothing,
    norm::AbstractNorm = InfNorm(),
    cache::NewtonCache = NewtonCache(F);
    options...
)
```

An implemenetation of a local Newton's method with various options to specify convergence criteria. Returns a [`NewtonResult`](@ref). The computations are always performed in complex arithmetic with double precision, i.e., using `Complex{Float64}`. The optional `cache` argument pre-allocates the necessary memory. This is useful if the method is called repeatedly.

### Options

  * `atol::Float64 = 1e-8`: The method is declared converged if `norm(xᵢ₊₁ - xᵢ) < atol`.
  * `rtol::Float64 = atol`: The method is declared converged if `norm(xᵢ₊₁ - xᵢ) < max(atol, rtol * norm(x₀))`.
  * `max_iters::Int = 20`: The maximal number of iterations.
  * `extended_precision::Bool = false`: An optional use of extended precision for the evaluation of `F(x)`. This can increase the achievable accuracy.
  * `contraction_factor::Float64 = 1.0`: The Newton updates have to satisfy $|xᵢ₊₁ - xᵢ| < a^{2^{i-1}}|x₁ - x₀|$ for $i ≥ 1$ where $a$ is `contraction_factor`.
  * `min_contraction_iters::Int = typemax(Int)`:  The minimal number of iterations the `contraction_factor` has to be satisfied. If after `min_contraction_iters` many iterations the contraction factor is not satisfied the step is accepted anyway.
  * `max_abs_norm_first_update::Float64 = Inf`: The initial guess `x₀` is rejected if `norm(x₁ - x₀) >  max_abs_norm_first_update`
  * `max_rel_norm_first_update::Float64 = max_abs_norm_first_update`: The initial guess `x₀` is rejected if `norm(x₁ - x₀) >  max_rel_norm_first_update * norm(x₀)`
