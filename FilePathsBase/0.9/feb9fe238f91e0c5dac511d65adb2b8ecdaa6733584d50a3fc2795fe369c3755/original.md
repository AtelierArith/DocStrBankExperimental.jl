```
extensions(fp::AbstractPath) -> AbstractString
```

Extracts all extensions from a filename if there any, otherwise it returns an empty string.

# Example

```jldoctest
julia> extensions(p"~/repos/FilePathsBase.jl/src/FilePathsBase.jl.bak")
2-element Array{SubString{String},1}:
 "jl"
 "bak"
```
