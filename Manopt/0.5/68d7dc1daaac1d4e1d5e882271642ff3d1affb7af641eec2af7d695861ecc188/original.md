```
AbstractGradientSolverState <: AbstractManoptSolverState
```

A generic [`AbstractManoptSolverState`](@ref) type for gradient based options data.

It assumes that

  * the iterate is stored in the field `p`
  * the gradient at `p` is stored in `X`.

# See also

[`GradientDescentState`](@ref), [`StochasticGradientDescentState`](@ref), [`SubGradientMethodState`](@ref), [`QuasiNewtonState`](@ref).
