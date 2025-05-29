```
tocxx(::Type{MyJuliaType})::String
```

ジュリア型から対応するC++型を文字列として返します。

```jldoctest
julia> using CxxCall: tocxx

julia> tocxx(Float64)
"double"

julia> tocxx(Int8)
"int8_t"
```
