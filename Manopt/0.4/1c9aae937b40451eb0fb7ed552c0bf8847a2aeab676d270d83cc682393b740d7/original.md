```
ConvexBundleMethodState <: AbstractManoptSolverState
```

Stores option values for a [`convex_bundle_method`](@ref) solver.

# Fields

  * `atol_λ`:                    (`eps()`) tolerance parameter for the convex coefficients in λ
  * `atol_errors`:               (`eps()`) tolerance parameter for the linearization errors
  * `bundle`:                    bundle that collects each iterate with the computed subgradient at the iterate
  * `bundle_cap`:                (`25`) the maximal number of elements the bundle is allowed to remember
  * `diameter`:                  (`50.0`) estimate for the diameter of the level set of the objective function at the starting point
  * `domain`:                    (`(M, p) -> isfinite(f(M, p))`) a function to that evaluates to true when the current candidate is in the domain of the objective `f`, and false otherwise, for example `domain = (M, p) -> p ∈ dom f(M, p) ? true : false`
  * `g`:                         descent direction
  * `inverse_retraction_method`: the inverse retraction to use within
  * `k_max`:                     upper bound on the sectional curvature of the manifold
  * `linearization_errors`:      linearization errors at the last serious step
  * `m`:                         (`1e-3`) the parameter to test the decrease of the cost: $f(q_{k+1}) \le f(p_k) + m \xi$.
  * `p`:                         current candidate point
  * `p_last_serious`:            last serious iterate
  * `retraction_method`:         the retraction to use within
  * `stop`:                      a [`StoppingCriterion`](@ref)
  * `transported_subgradients`:  subgradients of the bundle that are transported to `p_last_serious`
  * `vector_transport_method`:   the vector transport method to use within
  * `X`:                         (`zero_vector(M, p)`) the current element from the possible subgradients at `p` that was last evaluated.
  * `stepsize`:                  ([`ConstantStepsize`](@ref)`(M)`) a [`Stepsize`](@ref)
  * `ε`:                         convex combination of the linearization errors
  * `λ`:                         convex coefficients that solve the subproblem
  * `ξ`:                         the stopping parameter given by $ξ = -\lvert g\rvert^2 – ε$
  * `sub_problem`:               ([`convex_bundle_method_subsolver`]) a function that solves the sub problem on `M` given the last serious iterate `p_last_serious`, the linearization errors `linearization_errors`, and the transported subgradients `transported_subgradients`,
  * `sub_state`:                 an [`AbstractManoptSolverState`](@ref) for the subsolver

# Constructor

```
ConvexBundleMethodState(M::AbstractManifold, p; kwargs...)
```

with keywords for all fields with defaults besides `p_last_serious` which obtains the same type as `p`.     You can use for example `X=` to specify the type of tangent vector to use
