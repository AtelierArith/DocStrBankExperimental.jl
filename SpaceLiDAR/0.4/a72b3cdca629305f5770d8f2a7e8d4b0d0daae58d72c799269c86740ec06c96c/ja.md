```
bounds(granule::ICESat2_Granule)
```

グラニュールのバウンディングボックスを取得します。

!!! warning
    これは .h5 ファイルを開くため、遅くなります。


# 例

```julia
julia> bounds(g)
g = ICESat2_Granule()
```
