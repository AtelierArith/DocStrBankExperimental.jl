```julia
irf!(M, probs, theta, beta; scoring_function)

```

An in-place version of [`irf`](@ref). Provides efficient computation by mutating `probs` in-place, thus avoiding allocation of an output vector.

## Examples

```jldoctest
julia> beta = (a = 1.2, b = 0.3, t = zeros(3));

julia> probs = zeros(length(beta.t) + 1);

julia> irf!(GPCM, probs, 0.0, beta)
4-element Vector{Float64}:
 0.3961927292844976
 0.2764142877832629
 0.19284770477416754
 0.13454527815807202

julia> probs
4-element Vector{Float64}:
 0.3961927292844976
 0.2764142877832629
 0.19284770477416754
 0.13454527815807202
```
