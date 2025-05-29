```
bincenters(r::AbstractRange)::AbstractRange
```

`r` がビン境界のコレクションとして解釈される場合、`bincenters` はビンの中心を返します。

```jldoctest
julia> using RangeHelpers: bincenters

julia> bincenters(1:10.0)
1.5:1.0:9.5
```

関連情報として [`binwalls`](@ref) を参照してください。
