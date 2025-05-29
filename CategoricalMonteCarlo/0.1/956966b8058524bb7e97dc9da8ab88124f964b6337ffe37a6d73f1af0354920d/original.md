```
algorithm2_1!(p::Vector{T}, I::Vector{Int}, w::Vector{<:Real}) where {T<:Real}
```

Fill `p` with the probabilities that result from normalizing the weights `w[I]`. Note that `T` must be a type which is able to hold the result of `inv(one(T))`.

See also: [`algorithm2_1`](@ref)
