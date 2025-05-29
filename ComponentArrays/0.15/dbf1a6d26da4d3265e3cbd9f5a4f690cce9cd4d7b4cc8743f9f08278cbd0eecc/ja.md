```
x = ComponentVector(nt::NamedTuple)
x = ComponentVector(;kwargs...)
x = ComponentVector(data::AbstractVector, ax)
x = ComponentVector{T}(args...; kwargs...) where T
```

`ComponentVector` は一次元の `ComponentArray` のエイリアスです。
