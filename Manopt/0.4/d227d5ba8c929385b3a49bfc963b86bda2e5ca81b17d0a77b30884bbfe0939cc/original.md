```
PrimalDualManifoldSemismoothNewtonObjective{E<:AbstractEvaluationType, TC, LO, ALO, PF, DPF, PG, DPG, L} <: AbstractPrimalDualManifoldObjective{E, TC, PF}
```

Describes a Problem for the Primal-dual Riemannian semismooth Newton algorithm. [DiepeveenLellmann:2021](@cite)

# Fields

  * `cost`:                        $F + G(Λ(⋅))$ to evaluate interim cost function values
  * `linearized_operator`:         the linearization $DΛ(⋅)[⋅]$ of the operator $Λ(⋅)$.
  * `linearized_adjoint_operator`: the adjoint differential $(DΛ)^* :  \mathcal N → T\mathcal M$
  * `prox_F`:                      the proximal map belonging to $F$
  * `diff_prox_F`:                 the (Clarke Generalized) differential of the proximal maps of $F$
  * `prox_G_dual`:                 the proximal map belonging to $g_n^*$
  * `diff_prox_dual_G`:            the (Clarke Generalized) differential of the proximal maps of $G^\ast_n$
  * `Λ`:                           the exact forward operator. This operator is required if `Λ(m)=n` does not hold.

# Constructor

```
PrimalDualManifoldSemismoothNewtonObjective(cost, prox_F, prox_G_dual, forward_operator, adjoint_linearized_operator,Λ)
```
