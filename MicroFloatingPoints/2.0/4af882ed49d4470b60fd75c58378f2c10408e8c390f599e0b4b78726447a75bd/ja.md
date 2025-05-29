```
eligible_step(start::Floatmu{szE,szf}, stop::Floatmu{szE,szf}) where {szE,szf}
eligible_step(::Type{Floatmu{szE,szf}}, start::Float64, stop::Float64) where {szE,szf}
```

`[start,stop]` の範囲を反復するために許可される最小の `Floatmu{szE,szf}` ステップを返します。

# 例

```jldoctest
julia> eligible_step(Floatmu{2,2}(-0.5),Floatmu{2,2}(2.5))
0.5
```
