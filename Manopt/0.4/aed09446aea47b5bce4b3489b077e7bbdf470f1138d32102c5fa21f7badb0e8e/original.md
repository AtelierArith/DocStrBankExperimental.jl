```
DifferenceOfConvexProximalState{Type} <: AbstractSubProblemSolverState
```

A struct to store the current state of the algorithm as well as the form. It comes in two forms, depending on the realisation of the `subproblem`.

# Fields

  * `inverse_retraction_method`: (`default_inverse_retraction_method(M)`) an inverse retraction method to use within Frank Wolfe.
  * `retraction_method`:         (`default_retraction_method(M)`) a type of retraction
  * `p`, `q`, `r`:               the current iterate, the gradient step and the prox, respectively their type is set by initializing `p`
  * `stepsize`:                  ([`ConstantStepsize`](@ref)`(1.0)`) a [`Stepsize`](@ref) function to run the modified algorithm (experimental)
  * `stop`:                      ([`StopWhenChangeLess`](@ref)`(1e-8)`) a [`StoppingCriterion`](@ref)
  * `X`, `Y`:                    (`zero_vector(M,p)`) the current gradient and descent direction, respectively their common type is set by the keyword `X`
  * `sub_problem`:               an [`AbstractManoptProblem`](@ref) problem or a function `(M, p, X) -> q` or `(M, q, p, X)` for the a closed form solution of the sub problem
  * `sub_state`:                 an [`AbstractManoptSolverState`](@ref) for the subsolver or an [`AbstractEvaluationType`](@ref) in case the sub problem is provided as a function

# Constructor

```
DifferenceOfConvexProximalState(M, p; kwargs...)
```

## Keyword arguments

  * `X`, `retraction_method`, `inverse_retraction_method`, `stepsize` for the corresponding fields
  * `stoppping_criterion` for the [`StoppingCriterion`](@ref)
