```
sdftomol(::Type{T}, io::IO) -> T
sdftomol(io::IO) -> SDFMolGraph
sdftomol(::Type{T}, path::AbstractString) -> T
sdftomol(path::AbstractString) -> SDFMolGraph
```

Read a SDFile(.sdf or .mol) and parse it into a molecule object with the given type. The given argument should be a file input stream or a file path.
