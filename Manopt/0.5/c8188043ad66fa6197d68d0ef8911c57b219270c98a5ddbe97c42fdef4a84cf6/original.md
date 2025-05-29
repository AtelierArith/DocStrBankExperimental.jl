```
DifferenceOfConvexProximalState{P, T, Pr, St, S<:Stepsize, SC<:StoppingCriterion, RTR<:AbstractRetractionMethod, ITR<:AbstractInverseRetractionMethod}
    <: AbstractSubProblemSolverState
```

A struct to store the current state of the algorithm as well as the form. It comes in two forms, depending on the realisation of the `subproblem`.

# Fields

  * `inverse_retraction_method::AbstractInverseRetractionMethod`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `retraction_method::AbstractRetractionMethod`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate
  * `q::P`: a point on the manifold $\mathcal M$ storing the gradient step
  * `r::P`: a point on the manifold $\mathcal M$ storing the result of the proximal map
  * `stepsize::Stepsize`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `X`, `Y`: the current gradient and descent direction, respectively their common type is set by the keyword `X`
  * `sub_problem::Union{AbstractManoptProblem, F}`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `sub_state::Union{AbstractManoptProblem, F}`:  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.

# Constructor

```
DifferenceOfConvexProximalState(M::AbstractManifold, sub_problem, sub_state; kwargs...)
```

construct an difference of convex proximal point state

```
DifferenceOfConvexProximalState(M::AbstractManifold, sub_problem;
    evaluation=AllocatingEvaluation(), kwargs...
```

)

construct an difference of convex proximal point state, where `sub_problem` is a closed form solution with `evaluation` as type of evaluation.

## Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `sub_problem`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `sub_state`:  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.

# Keyword arguments

  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$to specify the initial value
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stepsize=`[`ConstantLength`](@ref)`()`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `stopping_criterion=`[StopWhenChangeLess`](@ref)`(1e-8)`: a functor indicating that the stopping criterion is fulfilled
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$to specify the representation of a tangent vector
