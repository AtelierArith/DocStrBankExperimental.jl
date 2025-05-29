```
ConjugateResidualState{T,R,TStop<:StoppingCriterion} <: AbstractManoptSolverState
```

A state for the [`conjugate_residual`](@ref) solver.

# Fields

  * `X::T`: the iterate
  * `r::T`: the residual $r = -b(p) - \mathcal A(p)[X]$
  * `d::T`: the conjugate direction
  * `Ar::T`, `Ad::T`: storages for $\mathcal A(p)[d]$, $\mathcal A(p)[r]$
  * `rAr::R`: internal field for storing $⟨ r, \mathcal A(p)[r] ⟩$
  * `α::R`: a step length
  * `β::R`: the conjugate coefficient
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled

# Constructor

```
ConjugateResidualState(TpM::TangentSpace,slso::SymmetricLinearSystemObjective; kwargs...)
```

Initialise the state with default values.

## Keyword arguments

  * `r=-`[`get_gradient`](@ref)`(TpM, slso, X)`
  * `d=copy(TpM, r)`
  * `Ar=`[`get_hessian`](@ref)`(TpM, slso, X, r)`
  * `Ad=copy(TpM, Ar)`
  * `α::R=0.0`
  * `β::R=0.0`
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(`[`manifold_dimension`](@extref `ManifoldsBase.manifold_dimension-Tuple{AbstractManifold}`)`(M)``)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-8)`: a functor indicating that the stopping criterion is fulfilled
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$

# See also

[`conjugate_residual`](@ref)
