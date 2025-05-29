```
tsample(::Type{T<:Real}=Int, A::AbstractArray, n_sim::Int; [dims=:], [n_cat=nothing], [chunksize=5000])
```

See `sample` for full documentation; identical in behavior except that thread-based parallelism is used to accelerate the computation.

The optional `chunksize` argument provides a fixed upper bound for the number of simulations to be passed to each thread. Depending on number of independent categorical distributions to be sample and number of simulations to be performed, a `chunksize` of `5000` is likely too conservative. The user is encouraged to try smaller chunk sizes.

See also: [`sample`](@ref), [`vsample`](@ref), [`vtsample`](@ref)
