```
AdaptiveRegularizationState{P,T} <: AbstractHessianSolverState
```

A state for the [`adaptive_regularization_with_cubics`](@ref) solver.

# Fields

  * `η1`, `η1`: bounds for evaluating the regularization parameter
  * `γ1`, `γ2`:  shrinking and expansion factors for regularization parameter `σ`
  * `H`: the current Hessian evaluation
  * `s`: the current solution from the subsolver
  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate
  * `q`: a point for the candidates to evaluate model and ρ
  * `X::T`: a tangent vector at the point $p$ on the manifold $\mathcal M$storing the gradient at the current iterate
  * `s`: the tangent vector step resulting from minimizing the model problem in the tangent space $T_{p}\mathcal M$
  * `σ`: the current cubic regularization parameter
  * `σmin`: lower bound for the cubic regularization parameter
  * `ρ_regularization`: regularization parameter for computing ρ. When approaching convergence ρ may be difficult to compute with numerator and denominator approaching zero. Regularizing the ratio lets ρ go to 1 near convergence.
  * `ρ`: the current regularized ratio of actual improvement and model improvement.
  * `ρ_denominator`: a value to store the denominator from the computation of ρ to allow for a warning or error when this value is non-positive.
  * `retraction_method::AbstractRetractionMethod`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `sub_problem::Union{AbstractManoptProblem, F}`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `sub_state::Union{AbstractManoptProblem, F}`:  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.

Furthermore the following integral fields are defined

# Constructor

```
AdaptiveRegularizationState(M, sub_problem, sub_state; kwargs...)
```

Construct the solver state with all fields stated as keyword arguments and the following defaults

## Keyword arguments

  * `η1=0.1`
  * `η2=0.9`
  * `γ1=0.1`
  * `γ2=2.0`
  * `σ=100/manifold_dimension(M)`
  * `σmin=1e-7
  * `ρ_regularization=1e3`
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(100)`: a functor indicating that the stopping criterion is fulfilled
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$
