```
step_stats(::StochasticStyle)
step_stats(::CompressionStrategy)
```

Return a tuple of stat names (`Symbol` or `String`) and a tuple of zeros of the same length. These will be reported as columns in the `DataFrame` returned by [`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem).
