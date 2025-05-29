```
RenyiDivergence(α::Real)
renyi_divergence(P, Q, α::Real)
```

Create a Rényi premetric of order α.

Rényi defined a spectrum of divergence measures generalising the Kullback–Leibler divergence (see `KLDivergence`). The divergence is not a semimetric as it is not symmetric. It is parameterised by a parameter α, and is equal to Kullback–Leibler divergence at α = 1:

At α = 0, $R_0(P | Q) = -log(sum_{i: p_i > 0}(q_i))$

At α = 1, $R_1(P | Q) = sum_{i: p_i > 0}(p_i log(p_i / q_i))$

At α = ∞, $R_∞(P | Q) = log(sup_{i: p_i > 0}(p_i / q_i))$

Otherwise $R_α(P | Q) = log(sum_{i: p_i > 0}((p_i ^ α) / (q_i ^ (α - 1))) / (α - 1)$

# Example:

```jldoctest
julia> x = reshape([0.1, 0.3, 0.4, 0.2], 2, 2);

julia> pairwise(RenyiDivergence(0), x, x)
2×2 Array{Float64,2}:
 0.0  0.0
 0.0  0.0

julia> pairwise(Euclidean(2), x, x)
2×2 Array{Float64,2}:
 0.0       0.577315
 0.655407  0.0
```
