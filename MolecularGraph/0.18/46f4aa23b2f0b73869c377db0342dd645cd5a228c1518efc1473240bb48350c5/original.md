```
rxntoreaction(::Type{T}, io::IO) -> T
rxntoreaction(io::IO) -> Reaction{SDFMolGraph}
rxntoreaction(::Type{T}, path::AbstractString) -> T
rxntoreaction(path::AbstractString) -> Reaction{SDFMolGraph}
```

Read a RXN file and parse it into a reaction object with the given type. The given argument should be a file input stream or a file path.
