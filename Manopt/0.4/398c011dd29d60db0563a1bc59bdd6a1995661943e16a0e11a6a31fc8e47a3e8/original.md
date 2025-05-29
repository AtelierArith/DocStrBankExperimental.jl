```
convex_bundle_method(M, f, ∂f, p)
```

perform a convex bundle method $p_{j+1} = \mathrm{retr}(p_k, -g_k)$, where $\mathrm{retr}$ is a retraction and

$$
g_k = \sum_{j\in J_k} λ_j^k \mathrm{P}_{p_k←q_j}X_{q_j},
$$

$p_k$ is the last serious iterate, $X_{q_j} ∈ ∂f(q_j)$, and the $λ_j^k$ are solutions to the quadratic subproblem provided by the [`convex_bundle_method_subsolver`](@ref).

Though the subdifferential might be set valued, the argument `∂f` should always return one element from the subdifferential, but not necessarily deterministic.

For more details, see [BergmannHerzogJasa:2024](@cite).

# Input

  * `M`:  a manifold $\mathcal M$
  * `f`:   a cost function $f:\mathcal M→ℝ$ to minimize
  * `∂f`: the subgradient $∂f: \mathcal M → T\mathcal M$ of f restricted to always only returning one value/element from the subdifferential. This function can be passed as an allocation function `(M, p) -> X` or a mutating function `(M, X, p) -> X`, see `evaluation`.
  * `p`:  (`rand(M)`) an initial value $p_0 ∈ \mathcal M$

# Optional

  * `atol_λ`:                    (`eps()`) tolerance parameter for the convex coefficients in λ.
  * `atol_errors`:               (`eps()`) tolerance parameter for the linearization errors.
  * `m`:                         (`1e-3`) the parameter to test the decrease of the cost: $f(q_{k+1}) \le f(p_k) + m \xi$.
  * `diameter`:                  (`50.0`) estimate for the diameter of the level set of the objective function at the starting point.
  * `domain`:                    (`(M, p) -> isfinite(f(M, p))`) a function to that evaluates to true when the current candidate is in the domain of the objective `f`, and false otherwise, for example domain = (M, p) -> p ∈ dom f(M, p) ? true : false.
  * `k_max`:                     upper bound on the sectional curvature of the manifold.
  * `evaluation`:                ([`AllocatingEvaluation`](@ref)) specify whether the subgradient works by  allocation (default) form `∂f(M, q)` or [`InplaceEvaluation`](@ref) in place, that is of the form `∂f!(M, X, p)`.
  * `inverse_retraction_method`: (`default_inverse_retraction_method(M, typeof(p))`) an inverse retraction method to use
  * `retraction_method`:         (`default_retraction_method(M, typeof(p))`) a `retraction(M, p, X)` to use.
  * `stopping_criterion`:        ([`StopWhenLagrangeMultiplierLess`](@ref)`(1e-8; names=["-ξ"])`) a functor, see [`StoppingCriterion`](@ref), indicating when to stop
  * `vector_transport_method`:   (`default_vector_transport_method(M, typeof(p))`) a vector transport method to use
  * `sub_problem`:               a function evaluating with new allocations that solves the sub problem on `M` given the last serious iterate `p_last_serious`, the linearization errors `linearization_errors`, and the transported subgradients `transported_subgradients`

# Output

the obtained (approximate) minimizer $p^*$, see [`get_solver_return`](@ref) for details
