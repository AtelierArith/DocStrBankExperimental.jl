```
algorithm2_1_algorithm3_ratio(I::Vector{Int}, w::Vector{<:Real}, r::Real)
```

Return a vector of probabilities, normalizing the components selected from `w` by the index set `I`, then spreading the probability mass `u = r / (1 + r)` across the 0 or more elements of `w[I]` which are equal to zero such that the ratio of the sum of (inititally) zero elements to the sum of non-zero elements is equal to `r`. If all values of `w[I]` are zero and `r ≠ 0`, a vector of uniform probability mass is returned. Equivalent to `algorithm3_ratio!(algorithm2_1(I, w), u)` but more efficient.

See also: [`algorithm2_1_algorithm3_ratio!`](@ref), [`algorithm2_1`](@ref),  [`algorithm3_ratio`](@ref)

# Examples

```jldoctest
julia> I = [1, 2, 5, 6]; w = [10, 0, 30, 40, 0, 20]; r = 1.0;

julia> algorithm2_1_algorithm3_ratio(I, w, r)
4-element Vector{Float64}:
 0.16666666666666666
 0.25
 0.25
 0.3333333333333333

julia> algorithm3_ratio!(algorithm2_1(I, w), r)
4-element Vector{Float64}:
 0.16666666666666666
 0.25
 0.25
 0.3333333333333333
```
