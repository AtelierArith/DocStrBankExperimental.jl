```
vsample(::Type{T<:Real}=Int, A::AbstractArray, n_sim::Int; [dims=:], [n_cat=nothing])
```

See `sample` for full documentation; identical in behavior except that the underlying Marsaglia sampler uses `LoopVectorization`. Sometimes, but not always, confers speedup.

See also: [`vtsample`](@ref), [`sample`](@ref), [`tsample`](@ref)
