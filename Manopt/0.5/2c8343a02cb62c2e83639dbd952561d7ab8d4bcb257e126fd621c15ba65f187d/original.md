```
proximal_bundle_method(M, f, ∂f, p=rand(M), kwargs...)
proximal_bundle_method!(M, f, ∂f, p, kwargs...)
```

perform a proximal bundle method $p^{(k+1)} = \operatorname{retr}_{p^{(k)}}(-d_k)$, where $\operatorname{retr}$ is a retraction and

$$
d_k = \frac{1}{\mu_k} \sum_{j\in J_k} λ_j^k \mathrm{P}_{p_k←q_j}X_{q_j},
$$

with $X_{q_j} ∈ ∂f(q_j)$, $p_k$ the last serious iterate, $\mu_k$ a proximal parameter, and the $λ_j^k$ as solutions to the quadratic subproblem provided by the sub solver, see for example the [`proximal_bundle_method_subsolver`](@ref).

Though the subdifferential might be set valued, the argument `∂f` should always return *one* element from the subdifferential, but not necessarily deterministic.

For more details see [HoseiniMonjeziNobakhtianPouryayevali:2021](@cite).

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `f`: a cost function $f: \mathcal M→ ℝ$ implemented as `(M, p) -> v`
  * `∂f`:  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.
  * `p`: a point on the manifold $\mathcal M$

# Keyword arguments

  * `α₀=1.2`:          initialization value for `α`, used to update `η`
  * `bundle_size=50`:  the maximal size of the bundle
  * `δ=1.0`:           parameter for updating `μ`: if $δ < 0$ then $μ = \log(i + 1)$, else $μ += δ μ$
  * `ε=1e-2`:          stepsize-like parameter related to the injectivity radius of the manifold
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `m=0.0125`:        a real number that controls the decrease of the cost function
  * `μ=0.5`:           initial proximal parameter for the subproblem
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stopping_criterion=`[`StopWhenLagrangeMultiplierLess`](@ref)`(1e-8)`[`|`](@ref StopWhenAny)[`StopAfterIteration`](@ref)`(5000)`: a functor indicating that the stopping criterion is fulfilled
  * `sub_problem=`[`proximal_bundle_method_subsolver`](@ref)`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `sub_state=`[`AllocatingEvaluation`](@ref):  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively.

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
