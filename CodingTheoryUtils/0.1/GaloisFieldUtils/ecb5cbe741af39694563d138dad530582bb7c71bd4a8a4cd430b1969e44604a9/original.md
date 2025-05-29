```
hex(v::Vector{F2})::String
```

Convert a binary vector over F2 to a hexadecimal string representation.

# Arguments

  * `v::Vector{F2}`: A binary vector over F2

# Returns

  * `String`: Hexadecimal string representation of the input vector

# Examples

```julia
julia> v = [F2(1), F2(0), F2(1), F2(0)]
julia> hex(v)
"a"  # 1010 in hex

julia> v = [F2(1), F2(1), F2(1), F2(1), F2(0), F2(0), F2(0), F2(0)]
julia> hex(v)
"f0"  # 11110000 in hex
```
