```
algorithm3_ratio!(p::Vector{T}, w::Vector{<:Real}, r::Real) where {T<:Real}
```

Normalize `w` to probabilities, storing the result in `p`, then spread the probability mass `u = r / (1 + r)` across the 0 or more elements of `w` such that the ratio of the sum of (inititally) zero elements to the sum of non-zero elements is equal to `r`. Note that `T` must be a type which is able to hold the result of `inv(one(T))`.

# Examples

```jldoctest
julia> w = [0, 10, 5, 1]; r = 1.0;

julia> algorithm3_ratio!(similar(w, Float64), w, r)
4-element Vector{Float64}:
 0.5
 0.3125
 0.15625
 0.03125
```
