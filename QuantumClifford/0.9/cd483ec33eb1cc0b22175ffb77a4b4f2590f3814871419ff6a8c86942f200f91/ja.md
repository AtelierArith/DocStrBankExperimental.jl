二つの演算子が可換かどうかを確認します。

`0x0` は可換の場合、`0x1` は反可換の場合です。

```jldoctest
julia> P"XX"*P"ZZ", P"ZZ"*P"XX"
(- YY, - YY)

julia> comm(P"ZZ", P"XX")
0x00

julia> comm(P"IZ", P"XX")
0x01
```

参照: [`comm!`](@ref)
