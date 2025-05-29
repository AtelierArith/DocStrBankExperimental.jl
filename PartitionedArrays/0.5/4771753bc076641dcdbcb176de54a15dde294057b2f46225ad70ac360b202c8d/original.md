```
DebugArray(a)
```

Create a `DebugArray{T,N}` data object from the items in collection `a`, where `T=eltype(a)` and `N=ndims(a)` . If `a::Array{T,N}`, then the result takes ownership of the input. Otherwise, a copy of the input is created.
