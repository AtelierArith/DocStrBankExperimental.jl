```
extrema_stats([::Type{T},] num_features::Int)
```

This function creates an OnlineStats.KahanVariance object for tracking the mean and variance for a vector. Any OnlineStats.Weight can be used. The default is OnlineStats.EqualWeight and OnlineStats.ExponentialWeight  if an integer or float is given as the weight. 

See also: [`extrema_stats`](@ref), [`LinearNormalization`](@ref)

# Examples

```jldoctest
julia> stats = gaussian_stats(Float32, 2, 1e-4)
Group
├─ KahanVariance: n=0 | value=1.0
└─ KahanVariance: n=0 | value=1.0

julia> fit!(stats, [1.0, 2.0])
Group
├─ KahanVariance: n=1 | value=1.0
└─ KahanVariance: n=1 | value=1.0

```
