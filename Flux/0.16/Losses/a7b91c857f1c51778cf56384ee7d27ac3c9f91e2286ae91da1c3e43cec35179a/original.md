```
kldivergence(ŷ, y; agg = mean, eps = eps(eltype(ŷ)))
```

Return the [Kullback-Leibler divergence](https://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence) between the given probability distributions.

The KL divergence is a measure of how much one probability distribution is different from the other. It is always non-negative, and zero only when both the distributions are equal.

# Example

```jldoctest
julia> p1 = [1 0; 0 1]
2×2 Matrix{Int64}:
 1  0
 0  1

julia> p2 = fill(0.5, 2, 2)
2×2 Matrix{Float64}:
 0.5  0.5
 0.5  0.5

julia> Flux.kldivergence(p2, p1) ≈ log(2)
true

julia> Flux.kldivergence(p2, p1; agg = sum) ≈ 2log(2)
true

julia> Flux.kldivergence(p2, p2; eps = 0)  # about -2e-16 with the regulator
0.0

julia> Flux.kldivergence(p1, p2; eps = 0)  # about 17.3 with the regulator
Inf
```
