```
StringMaxLength{T<:AbstractString,V} <: BoundString{T}
StringMaxLength{T,V}(x::AbstractString)
```

A string constraint for a value `x` of type `T` which length must be no more than `V` characters.

## Examples

```jldoctest
julia> StringMaxLength{String,5}("abc")
"abc"

julia> StringMaxLength{String,5}("abcdef")
ERROR: ConstraintError: constraints of type StringMaxLength violated.
Wrong value: length of the "abcdef" must be no more than 5 characters (6).
[...]
```
