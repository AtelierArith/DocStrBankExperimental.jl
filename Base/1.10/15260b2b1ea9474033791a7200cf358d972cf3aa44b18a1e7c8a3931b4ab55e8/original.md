```
@big_str str
```

Parse a string into a [`BigInt`](@ref) or [`BigFloat`](@ref), and throw an `ArgumentError` if the string is not a valid number. For integers `_` is allowed in the string as a separator.

# Examples

```jldoctest
julia> big"123_456"
123456

julia> big"7891.5"
7891.5

julia> big"_"
ERROR: ArgumentError: invalid number format _ for BigInt or BigFloat
[...]
```
