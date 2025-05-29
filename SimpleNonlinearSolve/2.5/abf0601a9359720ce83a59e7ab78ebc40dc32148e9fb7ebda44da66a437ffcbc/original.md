```
SimpleLimitedMemoryBroyden(;
    threshold::Union{Val, Int} = Val(27), linesearch = Val(false), alpha = nothing
)
```

A limited memory implementation of Broyden. This method applies the L-BFGS scheme to Broyden's method.

If the threshold is larger than the problem size, then this method will use `SimpleBroyden`.

### Keyword Arguments:

  * `linesearch`: If `linesearch` is `Val(true)`, then we use the `LiFukushimaLineSearch` line search else no line search is used. For advanced customization of the line search, use `Broyden` from `NonlinearSolve.jl`.
  * `alpha`: Scale the initial jacobian initialization with `alpha`. If it is `nothing`, we will compute the scaling using `2 * norm(fu) / max(norm(u), true)`.

!!! warning
    Currently `alpha` is only used for StaticArray problems. This will be fixed in the future.

