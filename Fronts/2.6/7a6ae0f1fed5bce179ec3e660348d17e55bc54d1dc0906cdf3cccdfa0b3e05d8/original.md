```
FiniteDifference([N; pre])
```

Finite difference–based algorithm.

# Arguments

  * `N=500`: number of points in the spatial grid.

# Keyword arguments

  * `pre=nothing`: set to `BoltzmannODE()` to speed up the solution of compatible `AbstractFiniteProblem`s.

See also: [`solve`](@ref), [`AbstractFiniteProblem`](@ref), [`BoltzmannODE`](@ref)
