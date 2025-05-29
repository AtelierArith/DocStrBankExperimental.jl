```
Cp = parametric_colorant(C::Type)
```

パラメトリックカラントタイプを返します。

# 例

```jldoctest; setup = :(using ColorTypes, ColorTypes.FixedPointNumbers)
julia> parametric_colorant(RGB)
RGB

julia> parametric_colorant(RGB{Float32})
RGB{Float32}

julia> parametric_colorant(BGR)
BGR

julia> parametric_colorant(RGB24) == RGB{N0f8}
true
```
