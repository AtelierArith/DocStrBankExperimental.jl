```
apply_depo_channel(ρ::MPO, p::Vector{Float64})
```

Apply a local depolarization channel to an MPO by modifying each site tensor according to the depolarization probability.

For each site, the channel acts as:

ρ[i] → (1 - p[i]) * ρ[i] + (p[i] / 2) * (ρ[i] * δ(s, s') * δ(s, s'))

where δ(s, s') is the delta tensor that contracts the site index with its primed counterpart.

# Arguments

  * `ρ::MPO`: The input Matrix Product Operator representing a density matrix.
  * `p::Vector{Float64}`: A vector of depolarization probabilities, one per site.

# Returns

An MPO with the depolarization channel applied on each site.
