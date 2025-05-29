```
binwalls(r::AbstractRange; first=true, last=true)::AbstractRange
```

もし `r` がビンの中心のコレクションとして解釈される場合、`binwalls` はビンの境界を返します。

```jldoctest
julia> using RangeHelpers: binwalls

julia> binwalls(0.0:2.0:10.0)
-1.0:2.0:11.0

julia> binwalls(0.0:2.0:10.0, first=false)
1.0:2.0:11.0

julia> binwalls(0.0:2.0:10.0, last=false)
-1.0:2.0:9.0
```

詳細は [`bincenters`](@ref) を参照してください。
