```
algorithm2_1_algorithm3!(p::Vector{T}, I::Vector{Int}, w::Vector{<:Real}, u::Real) where {T<:Real}
```

Normalize `w[I]` to probabilities, storing the result in `p`, then spreading probability mass `0 ≤ u ≤ 1` across the 0 or more elements of `w[I]` which are equal to zero. If all values of `w[I]` are zero and `u ≠ 0`, `p` will be filled with uniform probability mass. Note that `T` must be a type which is able to hold the result of `inv(one(T))`.

See also: [`algorithm2_1_algorithm3`](@ref)

# Examples

```jldoctest
julia> I = [1, 2, 5, 6]; w = [10, 0, 30, 40, 0, 20]; u = 0.5;

julia> algorithm2_1_algorithm3!(similar(I, Rational{Int}), I, w, u)
4-element Vector{Rational{Int64}}:
 1//6
 1//4
 1//4
 1//3
```
