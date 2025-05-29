```
algorithm3!(p::Vector{T}, u::Real) where {T<:Real}
```

Normalize `p` to probabilities, spreading probability mass `u` across the 0 or more elements of `p` which are equal to zero. If all values of `w` are zero and `u ≠ 0`, `p` will be filled with uniform probability mass. Note that `T` must be a type which is able to hold the result of `inv(one(T))`.

See also: [`algorithm3`](@ref), [`algorithm3_ratio!`](@ref)

# Examples

```jldoctest
julia> algorithm3!(Rational{Int}[0, 10, 5, 0], 0.5)
4-element Vector{Rational{Int64}}:
 1//4
 1//3
 1//6
 1//4
```
