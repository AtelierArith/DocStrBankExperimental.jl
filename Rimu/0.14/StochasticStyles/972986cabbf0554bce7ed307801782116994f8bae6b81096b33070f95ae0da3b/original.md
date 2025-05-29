```
IsDeterministic{T=Float64}(compression=NoCompression()) <: StochasticStyle{T}
```

Propagate with deterministic vector matrix multiplications. Stochastic compression of the resultant vector (after annihilations) can be triggered by setting the optional `compression` argument to a relevant [`CompressionStrategy`](@ref).

See also [`StochasticStyle`](@ref).
