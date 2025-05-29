```
TypstString <: AbstractString
TypstString(::Any; context...)
```

Format the value as a Typst formatted string.

Optional Julia settings and Typst parameters are passed to [`show(::IO, ::MIME"text/typst", ::Typst)`](@ref) in an `IOContext`. See also [`show_typst`](@ref) for a list of supported types.

!!! info
    This type implements the `String` interface. However, the interface is undocumented, which may result in unexpected behavior.


# Examples

```jldoctest
julia> TypstString(1)
typst"$1$"

julia> TypstString(1 + 2im; mode = math)
typst"(1 + 2i)"
```
