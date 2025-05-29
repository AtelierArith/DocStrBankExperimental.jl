```
ChambollePock(M, N, f, p, X, m, n, prox_G, prox_G_dual, adjoint_linear_operator; kwargs...)
ChambollePock!(M, N, f, p, X, m, n, prox_G, prox_G_dual, adjoint_linear_operator; kwargs...)
```

Perform the Riemannian Chambolle—Pock algorithm.

Given a `cost` function $\mathcal E:\mathcal M → ℝ$ of the form

$$
\mathcal f(p) = F(p) + G( Λ(p) ),
$$

where $F:\mathcal M → ℝ$, $G:\mathcal N → ℝ$, and $Λ:\mathcal M → \mathcal N$.

This can be done inplace of $p$.

# Input parameters

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `N::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `p`: a point on the manifold $\mathcal M$
  * `X`: a tangent vector at the point $p$ on the manifold $\mathcal M$
  * `m`: a point on the manifold $\mathcal M$
  * `n`: a point on the manifold $\mathcal N$
  * `adjoint_linearized_operator`:  the adjoint $DΛ^*$ of the linearized operator $DΛ: T_{m}\mathcal M → T_{Λ(m)}\mathcal N)$
  * `prox_F, prox_G_Dual`:          the proximal maps of $F$ and $G^\ast_n$

note that depending on the [`AbstractEvaluationType`](@ref) `evaluation` the last three parameters as well as the forward operator `Λ` and the `linearized_forward_operator` can be given as allocating functions `(Manifolds, parameters) -> result`  or as mutating functions `(Manifold, result, parameters)` -> result` to spare allocations.

By default, this performs the exact Riemannian Chambolle Pock algorithm, see the optional parameter `DΛ` for their linearized variant.

For more details on the algorithm, see [BergmannHerzogSilvaLouzeiroTenbrinckVidalNunez:2021](@cite).

# Keyword Arguments

  * `acceleration=0.05`: acceleration parameter
  * `dual_stepsize=1/sqrt(8)`: proximal parameter of the primal prox
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `inverse_retraction_method_dual=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(N, typeof(n))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `Λ=missing`: the (forward) operator $Λ(⋅)$ (required for the `:exact` variant)
  * `linearized_forward_operator=missing`: its linearization $DΛ(⋅)[⋅]$ (required for the `:linearized` variant)
  * `primal_stepsize=1/sqrt(8)`: proximal parameter of the dual prox
  * `relaxation=1.`: the relaxation parameter $γ$
  * `relax=:primal`: whether to relax the primal or dual
  * `variant=:exact` if `Λ` is missing, otherwise `:linearized`: variant to use. Note that this changes the arguments the `forward_operator` is called with.
  * `stopping_criterion=`[StopAfterIteration`](@ref)`(100)`: a functor indicating that the stopping criterion is fulfilled
  * `update_primal_base=missing`: function to update `m` (identity by default/missing)
  * `update_dual_base=missing`: function to update `n` (identity by default/missing)
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
  * `vector_transport_method_dual=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(N, typeof(n))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
