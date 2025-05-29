```
LinearModel([::Type,] ϕ, num_features; num_outputs=1, num_actions=1)
```

This creates a linear function that uses the basis function ϕ. It can have multiple outputs (num*outputs >1) and optionally make action dependent predictions (num*actions > 1)

See also: [`TileCodingModel`](@ref), [`TabularModel`](@ref)

# Examples

```jldoctest
julia> ϕ = x->[x, x^2];

julia> m = LinearModel(ϕ, 2);

julia> vec(params(m)) .= 1:length(params(m));

julia> m(2.0) # 1 * 2 + 2 * 2^2
10.0

julia> m = LinearModel(ϕ, 2, num_outputs=2,num_actions=3);

julia> vec(params(m)) .= 1:length(params(m));

julia> m(2.0)
2×3 Matrix{Float64}:
 14.0  38.0  62.0
 20.0  44.0  68.0

julia> m(2.0, 3)  # 3rd action prediction
2-element Vector{Float64}:
 62.0
 68.0

julia> v,g = value_withgrad(m, 2.0, 1);

julia> v
2-element Vector{Float64}:
 14.0
 20.0

julia> g
2×2×3 Array{Float64, 3}:
[:, :, 1] =
 2.0  4.0
 2.0  4.0

[:, :, 2] =
 0.0  0.0
 0.0  0.0

[:, :, 3] =
 0.0  0.0
 0.0  0.0
 
```
