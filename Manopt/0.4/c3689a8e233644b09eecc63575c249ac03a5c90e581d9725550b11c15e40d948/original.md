```
proximal_bundle_method(M, f, ∂f, p)
```

perform a proximal bundle method $p_{j+1} = \mathrm{retr}(p_k, -d_k)$, where

$$
d_k = \frac{1}{\mu_l} \sum_{j\in J_k} λ_j^k \mathrm{P}_{p_k←q_j}X_{q_j},
$$

where $X_{q_j}\in∂f(q_j)$, $\mathrm{retr}$ is a retraction, $p_k$ is the last serious iterate, $\mu_l$ is a proximal parameter, and the $λ_j^k$ are solutions to the quadratic subproblem provided by the [`proximal_bundle_method_subsolver`](@ref).

Though the subdifferential might be set valued, the argument `∂f` should always return *one* element from the subdifferential, but not necessarily deterministic.

For more details see [HoseiniMonjeziNobakhtianPouryayevali:2021](@cite).

# Input

  * `M`: a manifold $\mathcal M$
  * `f`: a cost function $F:\mathcal M → ℝ$ to minimize
  * `∂f`: the (sub)gradient $∂ f: \mathcal M → T\mathcal M$ of f restricted to always only returning one value/element from the subdifferential. This function can be passed as an allocation function `(M, p) -> X` or a mutating function `(M, X, p) -> X`, see `evaluation`.
  * `p`: an initial value $p ∈ \mathcal M$

# Optional

  * `m`: a real number that controls the decrease of the cost function
  * `evaluation`: ([`AllocatingEvaluation`](@ref)) specify whether the subgradient works by  allocation (default) form `∂f(M, q)` or [`InplaceEvaluation`](@ref) in place,  that is it is of the form `∂f!(M, X, p)`.
  * `inverse_retraction_method`: (`default_inverse_retraction_method(M, typeof(p))`) an inverse retraction method to use
  * `retraction`: (`default_retraction_method(M, typeof(p))`) a `retraction(M, p, X)` to use.
  * `stopping_criterion`: ([`StopWhenLagrangeMultiplierLess`](@ref)`(1e-8)`) a functor, see[`StoppingCriterion`](@ref), indicating when to stop.
  * `vector_transport_method`: (`default_vector_transport_method(M, typeof(p))`) a vector transport method to use

and the ones that are passed to [`decorate_state!`](@ref) for decorators.

# Output

the obtained (approximate) minimizer $p^*$, see [`get_solver_return`](@ref) for details
