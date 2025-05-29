```
convex_bundle_method(M, f, ∂f, p)
convex_bundle_method!(M, f, ∂f, p)
```

perform a convex bundle method $p^{(k+1)} = \operatorname{retr}_{p^{(k)}}(-g_k)$ where

$$
g_k = \sum_{j\in J_k} λ_j^k \mathrm{P}_{p_k←q_j}X_{q_j},
$$

and $p_k$ is the last serious iterate, $X_{q_j} ∈ ∂f(q_j)$, and the $λ_j^k$ are solutions to the quadratic subproblem provided by the [`convex_bundle_method_subsolver`](@ref).

Though the subdifferential might be set valued, the argument `∂f` should always return one element from the subdifferential, but not necessarily deterministic.

For more details, see [BergmannHerzogJasa:2024](@cite).

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `f`: a cost function $f: \mathcal M→ ℝ$ implemented as `(M, p) -> v`
  * `∂f`:  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.
  * `p`: a point on the manifold $\mathcal M$

# Keyword arguments

  * `atol_λ=eps()` : tolerance parameter for the convex coefficients in $λ$.
  * `atol_errors=eps()`: : tolerance parameter for the linearization errors.
  * `bundle_cap=25``
  * `m=1e-3`: : the parameter to test the decrease of the cost: $f(q_{k+1}) ≤ f(p_k) + m ξ$.
  * `diameter=50.0`: estimate for the diameter of the level set of the objective function at the starting point.
  * `domain=(M, p) -> isfinite(f(M, p))`: a function to that evaluates to true when the current candidate is in the domain of the objective `f`, and false otherwise.
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `k_max=0`: upper bound on the sectional curvature of the manifold.
  * `stepsize=`[`default_stepsize`](@ref)`(M, ConvexBundleMethodState)`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)* `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `stopping_criterion=`[`StopWhenLagrangeMultiplierLess`](@ref)`(1e-8)`[`|`](@ref StopWhenAny)[`StopAfterIteration`](@ref)`(5000)`: a functor indicating that the stopping criterion is fulfilled
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
  * `sub_state=`[`convex_bundle_method_subsolver`](@ref)`:  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.
  * `sub_problem=`[`AllocatingEvaluation`](@ref):  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively.

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
