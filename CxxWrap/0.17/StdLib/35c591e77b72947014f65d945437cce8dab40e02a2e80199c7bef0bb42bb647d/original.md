```
StdString(str::Union{Cstring, Base.CodeUnits, Vector{UInt8}, Ref{Int8}, Array{Int8}})
```

Create a `StdString` from the null-terminated character sequence.

If you want to  construct a `StdString` that includes the null-character ('\0') either use [`StdString(::String)`](@ref) or [`StdString(::Any, ::Int)`](@ref).

## Examples

```julia
julia> StdString(b"visible\0hidden")
"visible"
```
