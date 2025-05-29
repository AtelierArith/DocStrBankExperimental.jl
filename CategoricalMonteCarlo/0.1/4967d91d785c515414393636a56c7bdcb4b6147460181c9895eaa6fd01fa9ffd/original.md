```
algorithm3_ratio(w::Vector{<:Real}, r::Real)
```

Return a vector of probabilities created by normalizing `w` to probabilities, then spread the probability mass `u = r / (1 + r)` across the 0 or more elements of `w` which are equal to zero such that the ratio of the sum of (inititally) zero elements to the sum of non-zero elements is equal to `r`. If all values of `w` are zero and `r ≠ 0`, a vector of uniform probability mass is returned.

Mathematically, given:

𝐰 ∈ ℝᴺ, 0 ≤ wᵢ < ∞, r ∈ ℝ, 0 ≤ r ≤ Inf, J = {i : 𝐰ᵢ = 0}

```
pᵢ =
    Case 1: if J ≠ ∅
            (r / (1+r)) / |J|                     if i ∈ J
            (1 / (1+r)) * 𝐰ᵢ / ∑ᵢ₌₁ᴺ 𝐰ᵢ           otherwise
    Case 2: if J = {1,…,N}
            r / (r * N)                           Equivalent to 1/N if 𝐰 ≠ ̲0
```

See also: [`algorithm3_ratio!`](@ref), [`algorithm3`](@ref)

# Examples

```jldoctest
julia> w = Rational{Int}[1, 0, 3, 0, 5]; r = 3;

julia> p = algorithm3_ratio(w, r)
5-element Vector{Rational{Int64}}:
 1//36
 3//8
 1//12
 3//8
 5//36

julia> r′ = sum(p[findall(iszero, w)]) / sum(p[findall(!iszero, w)]); (r′, r′ == r)
(3//1, true)

julia> algorithm3(w, r / (1 + r))              # Note equivalence
5-element Vector{Rational{Int64}}:
 1//36
 3//8
 1//12
 3//8
 5//36

julia> algorithm3_ratio(w, Inf)                # r = Inf ⟹ u = 1
5-element Vector{Rational{Int64}}:
 0//1
 1//2
 0//1
 1//2
 0//1
```
