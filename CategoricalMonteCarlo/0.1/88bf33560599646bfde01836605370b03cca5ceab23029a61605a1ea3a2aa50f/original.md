```
algorithm3_ratio!(p::Vector{T}, r::Real) where {T<:Real}
```

Normalize `p` to probabilities, then spread the probability mass `u = r / (1 + r)` across the 0 or more elements of `p` such that the ratio of the sum of (inititally) zero elements to the sum of the non-zero elements is equal to `r`. Note that `T` must be a type which is able to hold the result of `inv(one(T))`.

See also: [`algorithm3_ratio`](@ref), [`algorithm3!`](@ref)
