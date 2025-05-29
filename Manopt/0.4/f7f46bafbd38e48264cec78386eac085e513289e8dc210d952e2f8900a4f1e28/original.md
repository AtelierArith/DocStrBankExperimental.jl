```
cma_es(M, f, p_m=rand(M); σ::Real=1.0, kwargs...)
```

Perform covariance matrix adaptation evolutionary strategy search for global gradient-free randomized optimization. It is suitable for complicated non-convex functions. It can be reasonably expected to find global minimum within 3σ distance from `p_m`.

Implementation is based on [Hansen:2023](@cite) with basic adaptations to the Riemannian setting.

# Input

  * `M`:      a manifold $\mathcal M$
  * `f`:      a cost function $f: \mathcal M→ℝ$ to find a minimizer $p^*$ for

# Optional

  * `p_m`:                (`rand(M)`) an initial point `p`
  * `σ`:                  (`1.0`) initial standard deviation
  * `λ`:                  (`4 + Int(floor(3 * log(manifold_dimension(M))))`population size (can be increased for a more thorough global search but decreasing is not recommended)
  * `tol_fun`:            (`1e-12`) tolerance for the `StopWhenPopulationCostConcentrated`, similar to absolute difference between function values at subsequent points
  * `tol_x`:              (`1e-12`) tolerance for the `StopWhenPopulationStronglyConcentrated`, similar to absolute difference between subsequent point but actually computed from distribution parameters.
  * `stopping_criterion`: (`default_cma_es_stopping_criterion(M, λ; tol_fun=tol_fun, tol_x=tol_x)`)
  * `retraction_method`:  (`default_retraction_method(M, typeof(p_m))`)
  * `vector_transport_method`: (`default_vector_transport_method(M, typeof(p_m))`)
  * `basis`               (`DefaultOrthonormalBasis()`) basis used to represent covariance in
  * `rng`:                (`default_rng()`) random number generator for generating new points on `M`

# Output

the obtained (approximate) minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details.
