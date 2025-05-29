```
bklMC(X::AbstractGraph, β::Real, iters::Integer; keywords...)
```

Same as [`standardMC`](@ref), but uses the rejection-free method by Bortz, Kalos and Lebowitz. Each step takes more time, but rejected moves are almost free, since they are skipped entirely. This function has a specialized version for [`DiscrGraph`](@ref) models.

The return values and the keyword arguments are the same as [`standardMC`](@ref), see the usage examples for that function.

Note that the number of iterations includes the rejected moves. This makes the results directly comparable with those of `standardMC`. It also means that increasing `β` at fixed `iters` will result in fewer steps being actually computed.
