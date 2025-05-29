```
λ(::Type{Floatmu{szE,szf}})  where {szE,szf}
```

`Floatmu{szE,szf}`型の最小の正の*正規*数を返します。

# 例

```jldoctest
julia> λ(Floatmu{2, 2})
1.0

julia> λ(Floatmu{8, 23})==floatmin(Float32)
true
```
