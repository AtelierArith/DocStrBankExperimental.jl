```
StringLowerCase{T<:AbstractString} <: BoundString{T}
StringLowerCase{T}(x::AbstractString)
```

A string constraint for a value `x` of type `T` which characters must be in lowercase.

## Examples

```jldoctest
julia> StringLowerCase{String}("abcdef")
"abcdef"

julia> StringLowerCase{String}("aBcdEf")
ERROR: ConstraintError: constraints of type StringLowerCase violated.
Wrong value: some characters of "aBcdEf" must be in lowercase (B,E).
[...]
```
