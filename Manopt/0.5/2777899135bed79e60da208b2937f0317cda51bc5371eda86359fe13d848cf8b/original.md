```
ChambollePockState <: AbstractPrimalDualSolverState
```

stores all options and variables within a linearized or exact Chambolle Pock.

# Fields

  * `acceleration::R`:    acceleration factor
  * `dual_stepsize::R`:   proximal parameter of the dual prox
  * `inverse_retraction_method::AbstractInverseRetractionMethod`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `inverse_retraction_method_dual::AbstractInverseRetractionMethod`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `m::P`:               base point on $\mathcal M$
  * `n::Q`:               base point on $\mathcal N$
  * `p::P`:               an initial point on $p^{(0)} ∈ \mathcal M$
  * `pbar::P`:            the relaxed iterate used in the next dual update step (when using `:primal` relaxation)
  * `primal_stepsize::R`: proximal parameter of the primal prox
  * `X::T`:               an initial tangent vector $X^{(0)} ∈ T_{p^{(0)}}\mathcal M$
  * `Xbar::T`:            the relaxed iterate used in the next primal update step (when using `:dual` relaxation)
  * `relaxation::R`:      relaxation in the primal relaxation step (to compute `pbar`:
  * `relax::Symbol:       which variable to relax (`:primal`or`:dual`:
  * `retraction_method::AbstractRetractionMethod`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `variant`:            whether to perform an `:exact` or `:linearized` Chambolle-Pock
  * `update_primal_base`: function `(pr, st, k) -> m` to update the primal base
  * `update_dual_base`:  function `(pr, st, k) -> n` to update the dual base
  * `vector_transport_method::AbstractVectorTransportMethodP`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
  * `vector_transport_method_dual::AbstractVectorTransportMethodP`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)

Here, `P` is a point type on $\mathcal M$, `T` its tangent vector type, `Q` a point type on $\mathcal N$, and `R<:Real` is a real number type

where for the last two the functions a [`AbstractManoptProblem`](@ref)`p`, [`AbstractManoptSolverState`](@ref)`o` and the current iterate `i` are the arguments. If you activate these to be different from the default identity, you have to provide `p.Λ` for the algorithm to work (which might be `missing` in the linearized case).

# Constructor

```
ChambollePockState(M::AbstractManifold, N::AbstractManifold;
    kwargs...
) where {P, Q, T, R <: Real}
```

# Keyword arguments

  * `n=``[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(N)`
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`
  * `m=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`
  * `acceleration=0.0`
  * `dual_stepsize=1/sqrt(8)`
  * `primal_stepsize=1/sqrt(8)`
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `inverse_retraction_method_dual=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(N, typeof(n))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `relaxation=1.0`
  * `relax=:primal`: relax the primal variable by default
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(300)`: a functor indicating that the stopping criterion is fulfilled
  * `variant=:exact`: run the exact Chambolle Pock by default
  * `update_primal_base=missing`
  * `update_dual_base=missing`
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
  * `vector_transport_method_dual=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(N, typeof(n))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)

if `Manifolds.jl` is loaded, `N` is also a keyword argument and set to `TangentBundle(M)` by default.
