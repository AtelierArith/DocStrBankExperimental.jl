```
vtargmin(f, A::AbstractArray, dims=:)
```

Return the index of the argument which minimizes `f` over the dimensions `dims`, which may be `::Int`, `::NTuple{M, Int} where {M}` or `::Colon`. Threaded.

See also: [`vargmin`](@ref)
