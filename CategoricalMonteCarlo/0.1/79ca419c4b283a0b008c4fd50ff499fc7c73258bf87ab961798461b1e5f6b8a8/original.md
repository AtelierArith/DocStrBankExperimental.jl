```
algorithm4!(𝐰₁::Vector{T}, 𝐰₂::Vector{<:Real}) where {T<:Real}
```

Fill `𝐰₁` with the probabilities which result from `algorithm4(𝐰₁, 𝐰₂)`. Note that `T` must be a type which is able to hold the result of `inv(one(T))`.

See also: [`algorithm4`](@ref)
