```
NaNμ(::Type{Floatmu{szE,szf}}) where {szE, szf}
```

`Floatmu{szE,szf}`形式のNaN。

標準的なNaN値は符号ビットがゼロに設定され、左端のビットを除いて小数部分のすべてのビットがゼロに設定されています。

# 例

```jldoctest
julia> isnan(NaNμ(Floatmu{2, 2}))
true
julia> NaNμ(Floatmu{2, 2})
NaNμ{2, 2}
```
