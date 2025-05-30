```
Bool <: Integer
```

ブール型で、値は `true` と `false` です。

`Bool` は数の一種です：`false` は数値的に `0` と等しく、`true` は数値的に `1` と等しいです。さらに、`false` は乗法的な「強いゼロ」として機能します：

```jldoctest
julia> false == 0
true

julia> true == 1
true

julia> 0 * NaN
NaN

julia> false * NaN
0.0
```

関連項目: [`digits`](@ref), [`iszero`](@ref), [`NaN`](@ref).
