```
action_distribution(dist::Type{T}, model_output) where {T<:DiscreteDistribution}
```

When `dist` is a subtype of `DiscreteDistribution`, assume `model_output` is a batch of unnormalized log probabilities.

# Examples

```jldoctest
julia> model_output = reshape(1:10, 5, 2)
5×2 reshape(::UnitRange{Int64}, 5, 2) with eltype Int64:
 1   6
 2   7
 3   8
 4   9
 5  10
julia> action_distribution(Categorical, model_output)
2-element Vector{Categorical{Float64, Vector{Float64}}}:
 Categorical{Float64, Vector{Float64}}(
support: Base.OneTo(5)
p: [0.011656230956039605, 0.03168492079612427, 0.0861285444362687, 0.23412165725273662, 0.6364086465588308]
)

 Categorical{Float64, Vector{Float64}}(
support: Base.OneTo(5)
p: [0.011656230956039605, 0.03168492079612427, 0.0861285444362687, 0.23412165725273662, 0.6364086465588308]
)
```
