```
ProximalBundleMethodState <: AbstractManoptSolverState
```

stores option values for a [`proximal_bundle_method`](@ref) solver.

# Fields

  * `approx_errors`:            approximation of the linearization errors at the last serious step
  * `bundle`:                   bundle that collects each iterate with the computed subgradient at the iterate
  * `bundle_size`:              (`50`) the maximal size of the bundle
  * `c`:                         convex combination of the approximation errors
  * `d`:                         descent direction
  * `inverse_retraction_method`: the inverse retraction to use within
  * `m`:                         (`0.0125`) the parameter to test the decrease of the cost
  * `p`:                         current candidate point
  * `p_last_serious`:            last serious iterate
  * `retraction_method`:         the retraction to use within
  * `stop`:                      a [`StoppingCriterion`](@ref)
  * `transported_subgradients`:  subgradients of the bundle that are transported to `p_last_serious`
  * `vector_transport_method`:   the vector transport method to use within
  * `X`:                         (`zero_vector(M, p)`) the current element from the possible subgradients at `p` that was last evaluated.
  * `α₀`:                        (`1.2`) initialization value for `α`, used to update `η`
  * `α`:                         curvature-dependent parameter used to update `η`
  * `ε`:                         (`1e-2`) stepsize-like parameter related to the injectivity radius of the manifold
  * `δ`:                         parameter for updating `μ`: if $δ < 0$ then $μ = \log(i + 1)$, else $μ += δ μ$
  * `η`:                         curvature-dependent term for updating the approximation errors
  * `λ`:                         convex coefficients that solve the subproblem
  * `μ`:                         (`0.5`) (initial) proximal parameter for the subproblem
  * `ν`:                         the stopping parameter given by $ν = - μ |d|^2 - c$
  * `sub_problem`:               a function evaluating with new allocations that solves the sub problem on `M` given the last serious iterate `p_last_serious`, the linearization errors `linearization_errors`, and the transported subgradients `transported_subgradients`,
  * `sub_state`:                 an [`AbstractManoptSolverState`](@ref) for the subsolver

# Constructor

```
ProximalBundleMethodState(M::AbstractManifold, p; kwargs...)
```

with keywords for all fields from before besides `p_last_serious` which obtains the same type as `p`. You can use for example `X=` to specify the type of tangent vector to use
