```
DouglasRachfordState <: AbstractManoptSolverState
```

Store all options required for the DouglasRachford algorithm,

# Fields

  * `p`:                         the current iterate (result) For the parallel Douglas-Rachford, this is not a value from the `PowerManifold` manifold but the mean.
  * `s`:                         the last result of the double reflection at the proximal maps relaxed by `α`.
  * `λ`:                         function to provide the value for the proximal parameter during the calls
  * `α`:                         relaxation of the step from old to new iterate, to be precise $x^{(k+1)} = g(α(k); x^{(k)}, t^{(k)})$, where $t^{(k)}$ is the result of the double reflection involved in the DR algorithm
  * `inverse_retraction_method`: an inverse retraction method
  * `R`:                          method employed in the iteration to perform the reflection of `x` at the prox `p`.
  * `reflection_evaluation`:     whether `R` works in-place or allocating
  * `retraction_method`:         a retraction method
  * `stop`:                      a [`StoppingCriterion`](@ref)
  * `parallel`:                  indicate whether to use a parallel Douglas-Rachford or not.

# Constructor

```
DouglasRachfordState(M, p; kwargs...)
```

Generate the options for a Manifold `M` and an initial point `p`, where the following keyword arguments can be used

  * `λ`:                    (`(iter)->1.0`) function to provide the value for the proximal parameter during the calls
  * `α`:                    (`(iter)->0.9`) relaxation of the step from old to new iterate, to be precise $x^{(k+1)} = g(α(k); x^{(k)}, t^{(k)})$, where $t^{(k)}$ is the result of the double reflection involved in the DR algorithm
  * `R`:                    ([`reflect`](@ref) or `reflect!`) method employed in the iteration to perform the reflection of `x` at the prox `p`, which function is used depends on `reflection_evaluation`.
  * `reflection_evaluation`: ([`AllocatingEvaluation`](@ref)`()`) specify whether the reflection works in-place or allocating (default)
  * `stopping_criterion`:   ([`StopAfterIteration`](@ref)`(300)`) a [`StoppingCriterion`](@ref)
  * `parallel`:             (`false`) indicate whether to use a parallel Douglas-Rachford or not.
