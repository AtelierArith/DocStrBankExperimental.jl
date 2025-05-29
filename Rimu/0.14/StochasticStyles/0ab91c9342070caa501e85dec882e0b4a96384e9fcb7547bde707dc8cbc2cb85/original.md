```
IsStochasticInteger{T=Int}() <: StochasticStyle{T}
```

FCIQMC algorithm with integer walkers as in [Booth *et al.* (2009)](https://doi.org/10.1063/1.3193710). During the vector matrix product each individual diagonal and spawning step is rounded stochastically to a nearby integer value.

See also [`StochasticStyle`](@ref).
