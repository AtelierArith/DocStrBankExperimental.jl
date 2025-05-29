```
ChambollePock(
    M, N, cost, x0, ξ0, m, n, prox_F, prox_G_dual, adjoint_linear_operator;
    forward_operator=missing,
    linearized_forward_operator=missing,
    evaluation=AllocatingEvaluation()
)
```

Perform the Riemannian Chambolle—Pock algorithm.

Given a `cost` function $\mathcal E:\mathcal M → ℝ$ of the form

$$
\mathcal E(p) = F(p) + G( Λ(p) ),
$$

where $F:\mathcal M → ℝ$, $G:\mathcal N → ℝ$, and $Λ:\mathcal M → \mathcal N$. The remaining input parameters are

  * `p, X`:                         primal and dual start points $x∈\mathcal M$ and $ξ∈T_n\mathcal N$
  * `m,n`:                          base points on $\mathcal M$ and $\mathcal N$, respectively.
  * `adjoint_linearized_operator`:  the adjoint $DΛ^*$ of the linearized operator $DΛ(m): T_{m}\mathcal M → T_{Λ(m)}\mathcal N$
  * `prox_F, prox_G_Dual`:          the proximal maps of $F$ and $G^\ast_n$

note that depending on the [`AbstractEvaluationType`](@ref) `evaluation` the last three parameters as well as the forward operator `Λ` and the `linearized_forward_operator` can be given as allocating functions `(Manifolds, parameters) -> result`  or as mutating functions `(Manifold, result, parameters)` -> result` to spare allocations.

By default, this performs the exact Riemannian Chambolle Pock algorithm, see the optional parameter `DΛ` for their linearized variant.

For more details on the algorithm, see [BergmannHerzogSilvaLouzeiroTenbrinckVidalNunez:2021](@cite).

# Optional parameters

  * `acceleration`:                (`0.05`)
  * `dual_stepsize`:               (`1/sqrt(8)`) proximal parameter of the primal prox
  * `evaluation`:                  ([`AllocatingEvaluation`](@ref)`()) specify whether the proximal maps and operators are allocating functions`(Manifolds, parameters) -> result`or  given as mutating functions`(Manifold, result, parameters)`-> result`
  * `Λ`:                           (`missing`) the (forward) operator $Λ(⋅)$ (required for the `:exact` variant)
  * `linearized_forward_operator`: (`missing`) its linearization $DΛ(⋅)[⋅]$ (required for the `:linearized` variant)
  * `primal_stepsize`:             (`1/sqrt(8)`) proximal parameter of the dual prox
  * `relaxation`:                  (`1.`) the relaxation parameter $γ$
  * `relax`:                       (`:primal`) whether to relax the primal or dual
  * `variant`:                     (`:exact` if `Λ` is missing, otherwise `:linearized`) variant to use. Note that this changes the arguments the `forward_operator` is called with.
  * `stopping_criterion`:          (`[StopAfterIteration`](@ref)`(100)`) a [`StoppingCriterion`](@ref)
  * `update_primal_base`:          (`missing`) function to update `m` (identity by default/missing)
  * `update_dual_base`:            (`missing`) function to update `n` (identity by default/missing)
  * `retraction_method`:           (`default_retraction_method(M, typeof(p))`) the retraction to use
  * `inverse_retraction_method`    (`default_inverse_retraction_method(M, typeof(p))`) an inverse retraction to use.
  * `vector_transport_method`      (`default_vector_transport_method(M, typeof(p))`) a vector transport to use

# Output

the obtained (approximate) minimizer $p^*$, see [`get_solver_return`](@ref) for details.
