```
StringFixedLength{T<:AbstractString,V} <: BoundString{T}
StringFixedLength{T,V}(x::AbstractString)
```

A string constraint for a value `x` of type `T` which length must be equal to `V` characters.

## Examples

```jldoctest
julia> StringFixedLength{String,5}("abcde")
"abcde"

julia> StringFixedLength{String,5}("abc")
ERROR: ConstraintError: constraints of type StringFixedLength violated.
Wrong value: length of the "abc" must be equal to 5 characters (3).
[...]
```
