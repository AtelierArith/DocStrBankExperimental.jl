```
algorithm4!(p::Vector{T}, 𝐰₁::Vector{<:Real}, 𝐰₂::Vector{<:Real}) where {T<:Real}
```

Fill `p` with the probabilities which result from `algorithm4(𝐰₁, 𝐰₂)`. Note that `T` must be a type which is able to hold the result of `inv(one(T))`.
