```
action_distribution(dist::Type{T}, model_output) where {T<:ContinuousDistribution}
```

When `dist` is a subtype of `ContinuousDistribution`, assume `model_output` are a batch of parameters to be supplied to `dist`.

# Examples

```jldoctest
julia> model_output = reshape(1:10, 2, 5)
2×5 reshape(::UnitRange{Int64}, 2, 5) with eltype Int64:
 1  3  5  7   9
 2  4  6  8  10
julia> action_distribution(Normal, model_output)
5-element Vector{Normal{Float64}}:
 Normal{Float64}(μ=1.0, σ=2.0)
 Normal{Float64}(μ=3.0, σ=4.0)
 Normal{Float64}(μ=5.0, σ=6.0)
 Normal{Float64}(μ=7.0, σ=8.0)
 Normal{Float64}(μ=9.0, σ=10.0)
```
