Check whether two operators commute.

`0x0` if they commute, `0x1` if they anticommute.

```jldoctest
julia> P"XX"*P"ZZ", P"ZZ"*P"XX"
(- YY, - YY)

julia> comm(P"ZZ", P"XX")
0x00

julia> comm(P"IZ", P"XX")
0x01
```

See also: [`comm!`](@ref)
