```
vtfindmax(f, A::AbstractArray, dims=:) -> (f(x), index)
```

Return the value and the index of the argument which maximizes `f` over the dimensions `dims`, which may be `::Int`, `::NTuple{M, Int} where {M}` or `::Colon`. Threaded.

See also: [`vfindmax`](@ref)

# Warning

`NaN` values are not handled!
