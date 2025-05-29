```
algorithm3(w::Vector{<:Real}, u::Real)
```

Return the vector of probabilities created by normalizing `w` to probabilities, then spreading the probability mass `0 ≤ u ≤ 1` across the 0 or more elements of `w` which are equal to zero. If all values of `w` are zero and `u ≠ 0`, a vector of uniform probability mass is returned.

Mathematically, given:

𝐰 ∈ ℝᴺ, 0 ≤ wᵢ < ∞, u ∈ ℝ, 0 ≤ u ≤ 1, J = {i : 𝐰ᵢ = 0}

```
pᵢ =
    Case 1: if J ≠ ∅
            u / |J|                     if i ∈ J
            (1 - u) * 𝐰ᵢ / ∑ᵢ₌₁ᴺ 𝐰ᵢ     otherwise
    Case 2: if J = {1,…,N}
            u / (u * N)                 Equivalent to 1/N if 𝐰 ≠ ̲0
```

See also: [`algorithm3!`](@ref), [`algorithm3_ratio`](@ref)

# Examples

```jldoctest
julia> algorithm3([0, 10, 5, 0], 0.5)
4-element Vector{Float64}:
 0.25
 0.3333333333333333
 0.16666666666666666
 0.25

julia> algorithm3(Rational{Int}[0, 0, 0], 0.25)    # 𝐰 = ̲0
3-element Vector{Rational{Int64}}:
 1//3
 1//3
 1//3

julia> algorithm3([0, 0], 0.0)                     # 𝐰 = ̲0 and u = 0
2-element Vector{Float64}:
 NaN
 NaN

julia> algorithm3([1, 2, 3], 0.9)                  # in absence of 0's, just normalize
3-element Vector{Float64}:
 0.16666666666666666
 0.3333333333333333
 0.5
```
