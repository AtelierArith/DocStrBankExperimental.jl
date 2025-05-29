```
DouglasRachfordState <: AbstractManoptSolverState
```

Store all options required for the DouglasRachford algorithm,

# Fields

  * `α`:                         relaxation of the step from old to new iterate, to be precise $x^{(k+1)} = g(α(k); x^{(k)}, t^{(k)})$, where $t^{(k)}$ is the result of the double reflection involved in the DR algorithm
  * `inverse_retraction_method::AbstractInverseRetractionMethod`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `λ`:                         function to provide the value for the proximal parameter during the calls
  * `parallel`:                  indicate whether to use a parallel Douglas-Rachford or not.
  * `R`:                          method employed in the iteration to perform the reflection of `x` at the prox `p`.
  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate For the parallel Douglas-Rachford, this is not a value from the `PowerManifold` manifold but the mean.
  * `reflection_evaluation`:     whether `R` works in-place or allocating
  * `retraction_method::AbstractRetractionMethod`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `s`:                         the last result of the double reflection at the proximal maps relaxed by `α`.
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled

# Constructor

```
DouglasRachfordState(M::AbstractManifold; kwargs...)
```

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$

# Keyword arguments

  * `α= k -> 0.9`: relaxation of the step from old to new iterate, to be precise $x^{(k+1)} = g(α(k); x^{(k)}, t^{(k)})$, where $t^{(k)}$ is the result of the double reflection involved in the DR algorithm
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `λ= k -> 1.0`: function to provide the value for the proximal parameter during the calls
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$to specify the initial value
  * `R=`[`reflect`](@ref)`(!)`: method employed in the iteration to perform the reflection of `p` at the prox of `p`, which function is used depends on `reflection_evaluation`.
  * `reflection_evaluation=`[`AllocatingEvaluation`](@ref)`()`) specify whether the reflection works in-place or allocating (default)
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(300)`: a functor indicating that the stopping criterion is fulfilled
  * `parallel=false`: indicate whether to use a parallel Douglas-Rachford or not.
