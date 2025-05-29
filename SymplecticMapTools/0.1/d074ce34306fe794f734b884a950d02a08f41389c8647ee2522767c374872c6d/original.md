```
newton_periodic(FJ::Function, x::AbstractVector, q::Integer;
                maxiter::Integer=50, rtol::Number=1e-8, verbose::Bool=false)
```

Find a periodic orbit using Newton's method with line search

Arguments:

  * `FJ`: A function that returns the map and its derivative `F, dFdx = FJ(x)`
  * `x`: An initial point to find the orbit from
  * `q`: The period of the orbit
  * `maxiter=50`: The maximum number of optimization steps allows
  * `rtol=1e-8`: The residual tolerance required
  * `verbose=false`: If true, outputs information about convergence

Output:

  * `xs`: A periodic trajectory of length `d`
  * `converged`: A flag that indicates whether the orbit converged in `maxiter` steps
