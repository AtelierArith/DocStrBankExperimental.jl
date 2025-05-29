```
extension(fp::AbstractPath) -> AbstractString
```

Extracts the last extension from a filename if there any, otherwise it returns an empty string.

# Example

```jldoctest
julia> extension(p"~/repos/FilePathsBase.jl/src/FilePathsBase.jl")
"jl"
```
