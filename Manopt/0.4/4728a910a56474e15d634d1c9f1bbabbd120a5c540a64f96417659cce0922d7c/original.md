```
primal_dual_semismooth_Newton(M, N, cost, p, X, m, n, prox_F, diff_prox_F, prox_G_dual, diff_prox_dual_G, linearized_operator, adjoint_linearized_operator)
```

Perform the Primal-Dual Riemannian semismooth Newton algorithm.

Given a `cost` function $\mathcal E: \mathcal M → \overline{ℝ}$ of the form

$$
\mathcal E(p) = F(p) + G( Λ(p) ),
$$

where $F: \mathcal M → \overline{ℝ}$, $G: \mathcal N → \overline{ℝ}$, and $\Lambda: \mathcal M → \mathcal N$. The remaining input parameters are

  * `p, X`:                          primal and dual start points $p∈\mathcal M$ and $X ∈ T_n\mathcal N$
  * `m,n`:                           base points on $\mathcal M$ and $\mathcal N$, respectively.
  * `linearized_forward_operator`:   the linearization $DΛ(⋅)[⋅]$ of the operator $Λ(⋅)$.
  * `adjoint_linearized_operator`:   the adjoint $DΛ^*$ of the linearized operator $DΛ(m):  T_{m}\mathcal M → T_{Λ(m)}\mathcal N$
  * `prox_F, prox_G_Dual`:           the proximal maps of $F$ and $G^\ast_n$
  * `diff_prox_F, diff_prox_dual_G`: the (Clarke Generalized) differentials of the proximal maps of $F$ and $G^\ast_n$

For more details on the algorithm, see [DiepeveenLellmann:2021](@cite).

# Optional parameters

  * `primal_stepsize`:           (`1/sqrt(8)`) proximal parameter of the primal prox
  * `Λ`:                         (`missing`) the exact operator, that is required if `Λ(m)=n` does not hold; `missing` indicates, that the forward operator is exact.
  * `dual_stepsize`:             (`1/sqrt(8)`) proximal parameter of the dual prox
  * `reg_param`:                 (`1e-5`) regularisation parameter for the Newton matrix Note that this changes the arguments the `forward_operator` is called.
  * `stopping_criterion`:        (`stopAtIteration(50)`) a [`StoppingCriterion`](@ref)
  * `update_primal_base`:        (`missing`) function to update `m` (identity by default/missing)
  * `update_dual_base`:          (`missing`) function to update `n` (identity by default/missing)
  * `retraction_method`:         (`default_retraction_method(M, typeof(p))`) the retraction to use
  * `inverse_retraction_method`: (`default_inverse_retraction_method(M, typeof(p))`) an inverse retraction to use.
  * `vector_transport_method`:   (`default_vector_transport_method(M, typeof(p))`) a vector transport to use

# Output

the obtained (approximate) minimizer $p^*$, see [`get_solver_return`](@ref) for details
