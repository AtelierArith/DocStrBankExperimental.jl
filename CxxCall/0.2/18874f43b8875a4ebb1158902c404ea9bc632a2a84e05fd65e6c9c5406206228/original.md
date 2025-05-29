```
tocxx(::Type{MyJuliaType})::String
```

Return the corresponding C++ type as a string from the julia type.

```jldoctest
julia> using CxxCall: tocxx

julia> tocxx(Float64)
"double"

julia> tocxx(Int8)
"int8_t"
```
