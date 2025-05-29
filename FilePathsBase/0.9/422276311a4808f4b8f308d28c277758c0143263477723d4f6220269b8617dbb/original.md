```
filename(fp::AbstractPath) -> AbstractString
```

Extracts the `basename` without the extension.

# Example

```jldoctest
julia> filename(p"~/repos/FilePathsBase.jl/src/FilePathsBase.jl")
"FilePathsBase"

julia> filename(p"~/Downloads/julia-1.4.0-linux-x86_64.tar.gz")
"julia-1.4.0-linux-x86_64.tar"
```
