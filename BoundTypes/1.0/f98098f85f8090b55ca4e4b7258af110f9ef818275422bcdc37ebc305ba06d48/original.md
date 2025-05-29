```
StringPattern{T<:AbstractString,P} <: BoundString{T}
StringPattern{T,P}(x::AbstractString)
```

A string constraint for a value `x` of type `T` which must match regex pattern `P`.

!!! note
    Use a helper function [`@pattern_str`](@ref) to pass a regex expression.


## Examples

```jldoctest
julia> StringPattern{String,pattern"^[a-zA-Z0-9_]+$"}("abcde")
"abcde"

julia> StringPattern{String,pattern"^[a-zA-Z0-9_]+$"}("abc+def")
ERROR: ConstraintError: constraints of type StringPattern violated.
Wrong value: "abc+def" must match to regex pattern /^[a-zA-Z0-9_]+$/.
[...]
```
