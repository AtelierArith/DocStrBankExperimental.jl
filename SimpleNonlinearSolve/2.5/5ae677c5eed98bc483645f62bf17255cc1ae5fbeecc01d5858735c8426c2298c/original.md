```
SimpleBroyden(; linesearch = Val(false), alpha = nothing)
```

A low-overhead implementation of Broyden. This method is non-allocating on scalar and static array problems.

### Keyword Arguments

  * `linesearch`: If `linesearch` is `Val(true)`, then we use the `LiFukushimaLineSearch` line search else no line search is used. For advanced customization of the line search, use `Broyden` from `NonlinearSolve.jl`.
  * `alpha`: Scale the initial jacobian initialization with `alpha`. If it is `nothing`, we will compute the scaling using `2 * norm(fu) / max(norm(u), true)`.
