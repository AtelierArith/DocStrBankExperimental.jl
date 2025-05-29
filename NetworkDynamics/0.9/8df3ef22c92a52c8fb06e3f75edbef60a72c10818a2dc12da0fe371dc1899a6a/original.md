```
indim(c::VertexModel)::Int
indim(c::EdgeModel)::@NamedTuple{src::Int,dst::Int}
```

Musst be called *after* [`hasinsym`](@ref)/[`hasindim`](@ref) returned true. Gives the input dimension(s).
