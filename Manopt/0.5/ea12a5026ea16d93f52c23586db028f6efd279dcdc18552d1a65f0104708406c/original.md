```
FrankWolfeState <: AbstractManoptSolverState
```

A struct to store the current state of the [`Frank_Wolfe_method`](@ref)

It comes in two forms, depending on the realisation of the `subproblem`.

# Fields

  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate
  * `X::T`: a tangent vector at the point $p$ on the manifold $\mathcal M$storing the gradient at the current iterate
  * `inverse_retraction_method::AbstractInverseRetractionMethod`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `vector_transport_method::AbstractVectorTransportMethodP`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
  * `sub_problem::Union{AbstractManoptProblem, F}`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `sub_state::Union{AbstractManoptProblem, F}`:  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `stepsize::Stepsize`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `retraction_method::AbstractRetractionMethod`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)

The sub task requires a method to solve

$$
   \operatorname*{arg\,min}_{q ∈ C} ⟨\operatorname{grad} f(p_k), \log_{p_k}q⟩.
$$

# Constructor

```
FrankWolfeState(M, sub_problem, sub_state; kwargs...)
```

Initialise the Frank Wolfe method state.

FrankWolfeState(M, sub_problem; evaluation=AllocatingEvaluation(), kwargs...)

Initialise the Frank Wolfe method state, where `sub_problem` is a closed form solution with `evaluation` as type of evaluation.

## Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `sub_problem`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `sub_state`:  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.

## Keyword arguments

  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$to specify the initial value
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-6)`: a functor indicating that the stopping criterion is fulfilled
  * `stepsize=`[`default_stepsize`](@ref)`(M, FrankWolfeState)`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$to specify the representation of a tangent vector

where the remaining fields from before are keyword arguments.
