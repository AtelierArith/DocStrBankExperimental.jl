```
algorithm4(𝐰₁::Vector{<:Real}, 𝐰₂::Vector{<:Real})
```

Return a vector of probabilities constructed according to the following algorithm:

Define:

I = {1,…,N}

J₁ = {i: 𝐰₁ᵢ = 0},    I₁′ = {i: 𝐰₁ᵢ ≠ 0} = I ∖ J₁

J₂ = {i: 𝐰₂ᵢ = 0},    I₂′ = {i: 𝐰₂ᵢ ≠ 0} = I ∖ J₂

𝐰₁ ∈ ℝᴺ : initial weights, 0 ≤ 𝐰₁ᵢ < Inf

𝐰₂ ∈ ℝᴺ : augment weights, 0 ≤ 𝐰₂ᵢ < Inf; a value of zero indicates no re-weight

Then:

pᵢ = 𝐰₁ᵢ / ∑ₗ₌₁ᴺ 𝐰₁ₗ,                                       i ∈ I ∖ I₂′

pᵢ = (𝐰₂ᵢ * ∑ₗ 𝐰₁ₗ, l ∈ I₂′) / (∑ₗ₌₁ᴺ 𝐰₂ₗ * ∑ₗ₌₁ᴺ 𝐰₁ₗ),     i ∈ I₂′

This algorithm can produce a wide variety of probability vectors as the result of the various combinations of intersections which can be formed from J₁, J₂, I₁′, and I₂′. However, complexity of outputs aside, the motivating concept is quite simple: take a vector of weights, `𝐰₁` and re-weight some subset (I₂′) of those weights using a second set of weights, `𝐰₂`, while preserving the proportion of probability mass derived from `𝐰₁`. That is, given `p = algorithm4(𝐰₁, 𝐰₂)`, the following relationships are preserved: `sum(p[J₂]) ≈ sum(𝐰₁[J₂]) / sum(𝐰₁[I₁′])`, `sum(w₁[J₂]) / sum(w₁[I₂′]) ≈ sum(p[J₂]) / sum(p[I₂′])`.

See also: [`algorithm4!`](@ref)

# Examples

```jldoctest
julia> w₁ = [1, 1, 1, 1, 0];

julia> algorithm4(w₁, [2, 1, 3, 4, 0])    # J₁ ∩ I₂′ = ∅
5-element Vector{Float64}:
 0.2
 0.1
 0.30000000000000004
 0.4
 0.0

julia> algorithm4(w₁, [2, 1, 3, 0, 5])    # J₂ = [4] not re-weighted; I₂′ re-weighted
5-element Vector{Float64}:
 0.13636363636363635
 0.06818181818181818
 0.20454545454545453
 0.25
 0.3409090909090909

julia> w₁ = [1, 1, 1, 0, 0];

julia> algorithm4(w₁, [2, 1, 3, 4, 0])    # J₂ = [5] not re-weighted; I₂′ re-weighted
5-element Vector{Float64}:
 0.2
 0.1
 0.30000000000000004
 0.4
 0.0

julia> w₁ = [1, 1, 0, 1, 0];

julia> algorithm4(w₁, [0, 1, 0, 4, 0])    # J₂ = [1,3,5] not re-weighted; I₂′ re-weighted
5-element Vector{Float64}:
 0.3333333333333333
 0.13333333333333333
 0.0
 0.5333333333333333
 0.0

julia> algorithm4(w₁, [0, 0, 3, 4, 0])    # J₂ = [1,2,5] not re-weighted; I₂′ re-weighted
5-element Vector{Float64}:
 0.3333333333333333
 0.3333333333333333
 0.14285714285714285
 0.19047619047619047
 0.0

julia> algorithm4(w₁, [2, 0, 3, 0, 0])    # J₂ = [2,4,5] not re-weighted; I₂′ re-weighted
5-element Vector{Float64}:
 0.13333333333333333
 0.3333333333333333
 0.2
 0.3333333333333333
 0.0
```
