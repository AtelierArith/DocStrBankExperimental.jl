```
primal_dual_semismooth_Newton(M, N, cost, p, X, m, n, prox_F, diff_prox_F, prox_G_dual, diff_prox_dual_G, linearized_operator, adjoint_linearized_operator)
```

Perform the Primal-Dual Riemannian semismooth Newton algorithm.

Given a `cost` function $\mathcal E: \mathcal M → \overline{ℝ}$ of the form

$$
\mathcal E(p) = F(p) + G( Λ(p) ),
$$

where $F: \mathcal M → \overline{ℝ}$, $G: \mathcal N → \overline{ℝ}$, and $Λ: \mathcal M → \mathcal N$. The remaining input parameters are

  * `p, X`:                          primal and dual start points $p∈\mathcal M$ and $X ∈ T_n\mathcal N$
  * `m,n`:                           base points on $\mathcal M$ and ``\mathcal N`, respectively.
  * `linearized_forward_operator`:   the linearization $DΛ(⋅)[⋅]$ of the operator $Λ(⋅)$.
  * `adjoint_linearized_operator`:   the adjoint $DΛ^*$ of the linearized operator $DΛ(m):  T_{m}\mathcal M → T_{Λ(m)}\mathcal N$
  * `prox_F, prox_G_Dual`:           the proximal maps of $F$ and $G^\ast_n$
  * `diff_prox_F, diff_prox_dual_G`: the (Clarke Generalized) differentials of the proximal maps of $F$ and $G^\ast_n$

For more details on the algorithm, see [DiepeveenLellmann:2021](@cite).

# Keyword arguments

  * `dual_stepsize=1/sqrt(8)`: proximal parameter of the dual prox
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `Λ=missing`: the exact operator, that is required if `Λ(m)=n` does not hold; `missing` indicates, that the forward operator is exact.
  * `primal_stepsize=1/sqrt(8)`: proximal parameter of the primal prox
  * `reg_param=1e-5`: regularisation parameter for the Newton matrix Note that this changes the arguments the `forward_operator` is called.
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(50)`: a functor indicating that the stopping criterion is fulfilled
  * `update_primal_base=missing`: function to update `m` (identity by default/missing)
  * `update_dual_base=missing`: function to update `n` (identity by default/missing)
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively.

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
