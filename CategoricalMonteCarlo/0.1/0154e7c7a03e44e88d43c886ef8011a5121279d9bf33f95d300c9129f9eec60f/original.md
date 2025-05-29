```
algorithm3!(p::Vector{T}, w::Vector{<:Real}, u::Real) where {T<:Real}
```

Normalize `w` to probabilities, storing the result in `p`, spreading probability mass `0 ≤ u ≤ 1` across the 0 or more elements of `w` which are equal to zero. If all values of `w` are zero and `u ≠ 0`, `p` will be filled with uniform probability mass. Note that `T` must be a type which is able to hold the result of `inv(one(T))`.

# Examples

```jldoctest
julia> w = [0, 10, 5, 1]; u = 0.5;

julia> algorithm3!(similar(w, Float64), w, u)
4-element Vector{Float64}:
 0.5
 0.3125
 0.15625
 0.03125
```
