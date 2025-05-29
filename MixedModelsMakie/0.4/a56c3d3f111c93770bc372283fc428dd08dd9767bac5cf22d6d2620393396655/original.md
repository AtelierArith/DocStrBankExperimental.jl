```
splomaxes!(f::Indexable, labels::AbstractVector{<:AbstractString},
           panel!::Function, args...;
           extraticks::Bool=false, kwargs...)
```

Populate f with a set of `(k*(k-1))/2` axes in a lower triangle for all pairs of `labels`, where `k` is the length of `labels`.  The `panel!` function should have the signature `panel!(ax::Axis, i::Integer, j::Integer, args...; kwargs...)` and should draw the [i,j] panel in `ax`.
