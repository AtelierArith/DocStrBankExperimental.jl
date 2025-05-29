```
SimpleHalley(autodiff)
SimpleHalley(; autodiff = nothing)
```

A low-overhead implementation of Halley's Method.

!!! note
    As part of the decreased overhead, this method omits some of the higher level error catching of the other methods. Thus, to see better error messages, use one of the other methods like `NewtonRaphson`.


### Keyword Arguments

  * `autodiff`: determines the backend used for the Jacobian. Defaults to  `nothing` (i.e. automatic backend selection). Valid choices include jacobian backends from `DifferentiationInterface.jl`.
