```
cma_es(M, f, p_m=rand(M); σ::Real=1.0, kwargs...)
```

Perform covariance matrix adaptation evolutionary strategy search for global gradient-free randomized optimization. It is suitable for complicated non-convex functions. It can be reasonably expected to find global minimum within 3σ distance from `p_m`.

Implementation is based on [Hansen:2023](@cite) with basic adaptations to the Riemannian setting.

# Input

  * `M`:      a manifold $\mathcal M$
  * `f`:      a cost function $f: \mathcal M→ℝ$ to find a minimizer $p^*$ for

# Keyword arguments

  * `p_m=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: an initial point `p`
  * `σ=1.0`: initial standard deviation
  * `λ`:                  (`4 + Int(floor(3 * log(manifold_dimension(M))))`population size (can be increased for a more thorough global search but decreasing is not recommended)
  * `tol_fun=1e-12`: tolerance for the `StopWhenPopulationCostConcentrated`, similar to absolute difference between function values at subsequent points
  * `tol_x=1e-12`: tolerance for the `StopWhenPopulationStronglyConcentrated`, similar to absolute difference between subsequent point but actually computed from distribution parameters.
  * `stopping_criterion=``default_cma_es_stopping_criterion(M, λ; tol_fun=tol_fun, tol_x=tol_x)`: a functor indicating that the stopping criterion is fulfilled
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
  * `basis`               (`DefaultOrthonormalBasis()`) basis used to represent covariance in
  * `rng=default_rng()`: random number generator for generating new points on `M`

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively.

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
