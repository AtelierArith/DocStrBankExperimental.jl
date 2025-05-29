```julia
mutable struct FoldProblemMinimallyAugmented{Tprob<:BifurcationKit.AbstractBifurcationProblem, vectype, T<:Real, S<:BifurcationKit.AbstractLinearSolver, Sa<:BifurcationKit.AbstractLinearSolver, Sbd<:BifurcationKit.AbstractBorderedLinearSolver, Sbda<:BifurcationKit.AbstractBorderedLinearSolver, Tmass, Tn} <: BifurcationKit.AbstractProblemMinimallyAugmented{Tprob<:BifurcationKit.AbstractBifurcationProblem}
```

Structure to encode Fold / Hopf functional based on a Minimally Augmented formulation.

# Fields

  * `prob_vf`: Functional F(x, p) - vector field - with all derivatives.
  * `a`: close to null vector of Jᵗ.
  * `b`: close to null vector of J.
  * `zero`: vector zero, to avoid allocating it many times.
  * `l1`: Lyapunov coefficient.
  * `CP`: Cusp test value.
  * `BT`: Bogdanov-Takens test value.
  * `GH`: Bautin test values.
  * `ZH`: Zero-Hopf test values.
  * `linsolver`: linear solver. Used to invert the jacobian of MA functional.
  * `linsolverAdjoint`: linear solver for the jacobian adjoint.
  * `linbdsolver`: bordered linear solver.
  * `linbdsolverAdjoint`: linear bordered solver for the jacobian adjoint.
  * `usehessian`: whether to use the hessian of prob_vf.
  * `massmatrix`: whether to use a mass matrix M for studying M⋅∂ₜu = F(u), default = I.
  * `norm`: norm to normalize vector in update or test
  * `update_minaug_every_step`: Update the problem every such step
