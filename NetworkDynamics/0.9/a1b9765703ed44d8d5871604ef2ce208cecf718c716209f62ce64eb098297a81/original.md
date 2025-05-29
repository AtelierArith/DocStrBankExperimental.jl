```
insym(c::VertexModel)::Vector{Symbol}
insym(c::EdgeModel)::@NamedTuple{src::Vector{Symbol}, dst::Vector{Symbol}}
```

Musst be called *after* [`hasinsym`](@ref)/[`hasindim`](@ref) returned true. Gives the `insym` vector(s). For vertex model just a single vector, for edges it returns a named tuple `(; src, dst)` with two symbol vectors.
