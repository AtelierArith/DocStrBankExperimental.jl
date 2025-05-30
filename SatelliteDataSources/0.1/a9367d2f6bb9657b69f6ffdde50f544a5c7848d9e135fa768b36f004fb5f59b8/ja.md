```
translate_color(::Type{AbstractSatellite}, layer::Symbol)
```

`:red`、`:green`、または`:blue`のような色を対応するバンド名に変換します。

# 例

```julia
julia> translate_color(Landsat8, :red)
:B4

julia> translate_color(Sentinel2{10}, :nir)
:B08

julia> translate_color(Sentinel2{20}, :nir)
:B8A
```
