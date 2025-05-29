```
algorithm2_1(I::Vector{Int}, w::Vector{<:Real})
```

Create a vector of probabilities by normalizing the weights selected by `I` from `w`. It is assumed that `0 ≤ wᵢ < Inf, i ∈ I`.

Mathematically, given:

I ∈ ℕᴺ, 𝐰 ∈ ℝᴰ; I ⊆ {1,…,D}

The iᵗʰ term will be computed as: pᵢ = 𝐰ᵢ / ∑ⱼ 𝐰ⱼ; j ∈ I

See also: [`algorithm2_1!`](@ref), [`algorithm2_2`](@ref)

# Examples

```jldoctest
julia> I = [1, 5, 2]; w = [5, 4, 3, 2, 1];

julia> algorithm2_1(I, w)
3-element Vector{Float64}:
 0.5
 0.1
 0.4

julia> algorithm2_1([1, 1, 2], Rational.(w))
3-element Vector{Rational{Int64}}:
 5//14
 5//14
 2//7

julia> w[2] = -w[2];

julia> algorithm2_1(I, w)                # Nonsense results if `wᵢ` constraints violated
3-element Vector{Float64}:
  2.5
  0.5
 -2.0

julia> algorithm2_1(I, [5, 4, 3, 2, Inf])
3-element Vector{Float64}:
   0.0
 NaN
   0.0

julia> algorithm2_1(I, [5, NaN, 3, 2, 1])
3-element Vector{Float64}:
 NaN
 NaN
 NaN
```
