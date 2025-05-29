```
Typst{T}
Typst(::T)
```

A wrapper used to pass values to [`show(::IO, ::MIME"text/typst", ::Typst)`](@ref).

# Examples

```jldoctest
julia> Typst(1)
Typst{Int64}(1)

julia> Typst("a")
Typst{String}("a")
```
