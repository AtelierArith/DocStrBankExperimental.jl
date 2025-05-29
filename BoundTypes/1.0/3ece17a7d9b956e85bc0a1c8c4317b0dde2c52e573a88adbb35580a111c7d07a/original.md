```
StringMinLength{T<:AbstractString,V} <: BoundString{T}
StringMinLength{T,V}(x::AbstractString)
```

A string constraint for a value `x` of type `T` which length must be at least `V` characters.

## Examples

```jldoctest
julia> StringMinLength{String,5}("abcdef")
"abcdef"

julia> StringMinLength{String,5}("abc")
ERROR: ConstraintError: constraints of type StringMinLength violated.
Wrong value: length of the "abc" must be at least 5 characters (3).
[...]
```
