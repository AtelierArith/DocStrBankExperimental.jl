```
PrimalDualSemismoothNewtonState <: AbstractPrimalDualSolverState
```

  * `m`:                         base point on $\mathcal M$
  * `n`:                         base point on $\mathcal N$
  * `x`:                         an initial point on $x^{(0)} ∈ \mathcal M$ (and its previous iterate)
  * `ξ`:                         an initial tangent vector $\xi^{(0)} ∈ T_{n}^*\mathcal N$ (and its previous iterate)
  * `primal_stepsize`:           (`1/sqrt(8)`) proximal parameter of the primal prox
  * `dual_stepsize`:             (`1/sqrt(8)`) proximal parameter of the dual prox
  * `reg_param`:                 (`1e-5`) regularisation parameter for the Newton matrix
  * `stop`:                      a [`StoppingCriterion`](@ref)
  * `update_primal_base`:        (`( amp, ams, i) -> o.m`) function to update the primal base
  * `update_dual_base`:          (`(amp, ams, i) -> o.n`) function to update the dual base
  * `retraction_method`:         (`default_retraction_method(M, typeof(p))`) the retraction to use
  * `inverse_retraction_method`: (`default_inverse_retraction_method(M, typeof(p))`) an inverse retraction to use.
  * `vector_transport_method`:   (`default_vector_transport_method(M, typeof(p))`) a vector transport to use

where for the update functions a [`AbstractManoptProblem`](@ref) `amp`, [`AbstractManoptSolverState`](@ref) `ams` and the current iterate `i` are the arguments. If you activate these to be different from the default identity, you have to provide `p.Λ` for the algorithm to work (which might be `missing`).

# Constructor

```
PrimalDualSemismoothNewtonState(M::AbstractManifold,
    m::P, n::Q, x::P, ξ::T, primal_stepsize::Float64, dual_stepsize::Float64, reg_param::Float64;
    stopping_criterion::StoppingCriterion = StopAfterIteration(50),
    update_primal_base::Union{Function,Missing} = missing,
    update_dual_base::Union{Function,Missing} = missing,
    retraction_method = default_retraction_method(M, typeof(p)),
    inverse_retraction_method = default_inverse_retraction_method(M, typeof(p)),
    vector_transport_method = default_vector_transport_method(M, typeof(p)),
)
```
