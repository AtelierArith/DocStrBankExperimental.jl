```
quint2uint(qs::String, U::Type{T}=UInt) where T<:Unsigned
```

Convert a proquint string identifier `qs` into a corresponding integer value.

# Arguments

  * `U`: unsigned integer type e.g. `UInt16`, `UInt32`, `UInt64` or `UInt128`

# Example

```julia
julia> quint2uint("lusab-babad", UInt32)
0x7f000001

julia> quint2uint("lusab-d", UInt32)
0x7f000001
```
