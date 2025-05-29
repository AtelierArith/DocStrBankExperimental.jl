```
crs(x::Raster)
```

`Y` または `X` `Dimension` の投影座標参照系、または `AbstractRaster` の `Y`/`X` 次元の投影座標参照系を取得します。

[`Mapped`](@ref) の場合、投影座標参照系が全く存在しない可能性があるため、これは `nothing` である場合があります。手動で設定するには [`setcrs`](@ref) を参照してください。
