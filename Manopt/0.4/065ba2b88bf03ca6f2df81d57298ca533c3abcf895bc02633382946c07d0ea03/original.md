```
ConjugateResidualState{T,R,TStop<:StoppingCriterion} <: AbstractManoptSolverState
```

A state for the [`conjugate_residual`](@ref) solver.

# Fields

  * `X::T`: the iterate
  * `r::T`: the residual $r = -b(p) - \mathcal A(p)[X]$
  * `d::T`: the conjugate direction
  * `Ar::T`, `Ad::T`: storages for $\mathcal A$
  * `rAr::R`: internal field for storing $⟨ r, \mathcal A(p)[r] ⟩$
  * `α::R`: a step length
  * `β::R`: the conjugate coefficient
  * `stop::TStop`: a [`StoppingCriterion`](@ref) for the solver

# Constructor

```
    function ConjugateResidualState(
        TpM::TangentSpace,
        slso::SymmetricLinearSystemObjective;
        X=rand(TpM),
        r=-get_gradient(TpM, slso, X),
        d=copy(TpM, r),
        Ar=get_hessian(TpM, slso, X, r),
        Ad=copy(TpM, Ar),
        α::R=0.0,
        β::R=0.0,
        stopping_criterion=StopAfterIteration(manifold_dimension(TpM)) |
                           StopWhenGradientNormLess(1e-8),
        kwargs...,
)

Initialise the state with default values.
```
