```
simulate(εs::AbstractArray, r::VectorAutoregression, Y0=nothing; kwargs...)
```

Same as [`simulate!`](@ref), but makes a copy of `εs` for results and hence does not overwrite `εs`.
