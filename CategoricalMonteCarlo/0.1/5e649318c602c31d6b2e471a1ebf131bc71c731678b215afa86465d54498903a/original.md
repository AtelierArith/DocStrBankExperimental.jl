```
algorithm2_1_algorithm3(I::Vector{Int}, w::Vector{<:Real}, u::Real)
```

Return a vector of probabilities, normalizing the components selected from `w` by the index set `I`, then spreading the probability mass `0 ≤ u ≤ 1` across the 0 or more elements which are equal to zero. If all values of `w[I]` are zero and `u ≠ 0`, a vector of uniform probability mass is returned. Equivalent to `algorithm3!(algorithm2_1(I, w), u)` but more efficient.

See also: [`algorithm2_1_algorithm3!`](@ref), [`algorithm2_1`](@ref), [`algorithm3`](@ref)

# Examples

```jldoctest
julia> I = [1, 2, 5, 6]; w = [10, 0, 30, 40, 0, 20]; u = 0.5;

julia> algorithm2_1_algorithm3(I, w, u)
4-element Vector{Float64}:
 0.16666666666666666
 0.25
 0.25
 0.3333333333333333

julia> algorithm3!(algorithm2_1(I, w), u)
4-element Vector{Float64}:
 0.16666666666666666
 0.25
 0.25
 0.3333333333333333
```
