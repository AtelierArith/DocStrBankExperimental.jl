```
TypstText{T}
TypstText(::Any)
```

A wrapper whose [`show_typst`](@ref) method uses `print`.

# Examples

```jldoctest
julia> TypstText(1)
TypstText{Int64}(1)

julia> TypstText("a")
TypstText{String}("a")
```
