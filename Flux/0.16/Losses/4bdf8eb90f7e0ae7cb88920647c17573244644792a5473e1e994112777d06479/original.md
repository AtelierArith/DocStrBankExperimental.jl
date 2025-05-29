```
msle(ŷ, y; agg = mean, eps = eps(eltype(ŷ)))
```

The loss corresponding to mean squared logarithmic errors, calculated as

```
agg((log.(ŷ .+ ϵ) .- log.(y .+ ϵ)) .^ 2)
```

The `ϵ == eps` term provides numerical stability. Penalizes an under-estimation more than an over-estimatation.

# Example

```jldoctest
julia> Flux.msle(Float32[1.1, 2.2, 3.3], 1:3)
0.009084041f0

julia> Flux.msle(Float32[0.9, 1.8, 2.7], 1:3)
0.011100831f0
```
