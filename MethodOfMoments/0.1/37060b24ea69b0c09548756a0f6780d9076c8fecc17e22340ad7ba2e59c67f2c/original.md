```
fit!(m::NonlinearGMM{<:IteratedGMM}; kwargs...)
fit!(m::LinearGMM{<:IteratedLinearGMM}; kwargs...)
```

An in-place version of [`fit`](@ref) for proceeding with the iteration.
