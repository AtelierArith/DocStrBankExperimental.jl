```
TypstCommand(::AbstractVector{<:AbstractString})
TypstCommand(::TypstCommand; kwargs...)
```

The Typst compiler and its parameters.

Keyword parameters have the same semantics as for a `Cmd`.

!!! info
    This type implements the `Cmd` interface. However, the interface is undocumented, which may result in unexpected behavior.


# Examples

```jldoctest
julia> help = TypstCommand(["help"])
typst`help`

julia> TypstCommand(help; ignorestatus = true)
typst`help`
```
