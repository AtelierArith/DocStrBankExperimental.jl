```
convert_attribute(value, attribute::Key[, plottype::Key])
```

`value`を`attribute`として使用するのに適したドメインに変換します。

# 例

```jldoctest
julia> using Makie

julia> Makie.convert_attribute(:black, key"color"())
RGBA{Float32}(0.0f0,0.0f0,0.0f0,1.0f0)
```
