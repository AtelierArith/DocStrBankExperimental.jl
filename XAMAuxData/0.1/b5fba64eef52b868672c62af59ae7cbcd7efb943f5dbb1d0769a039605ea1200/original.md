```
AuxTag(::Union{String, SubString{String}})
AuxTag(::Char, ::Char)
AuxTag(::UInt8, ::UInt8)
```

The type of a key of `Auxiliary`. This type is lightweight, and validates that the key is of appropriate format. `Auxiliary` can also be modified using strings as keys, which will be converted to `AuxTag`, but this may cause a needless allocation of the string.

# Examples

```jldoctest
julia> AuxTag("AC")
AuxTag("AC")

julia> AuxTag('k', 'w')
AuxTag("kw")

julia> AuxTag("1C") # invalid tag
ERROR: Invalid AuxTag. Tags must conform to r"^[A-Za-z][A-Za-z0-9]$".
[...]
```
