```
StringUpperCase{T<:AbstractString} <: BoundString{T}
StringUpperCase{T}(x::AbstractString)
```

A string constraint for a value `x` of type `T` which characters must be in uppercase.

## Examples

```jldoctest
julia> StringUpperCase{String}("ABCDEF")
"ABCDEF"

julia> StringUpperCase{String}("AbCDeF")
ERROR: ConstraintError: constraints of type StringUpperCase violated.
Wrong value: some characters of "AbCDeF" must be in uppercase (b,e).
[...]
```
