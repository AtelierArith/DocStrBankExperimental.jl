```
classify(granule::ICESat2_Granule{:ATL03}, atl08::Union{ICESat2_Granule{:ATL08},Nothing} = nothing, tracks = icesat2_tracks)
```

[`points(::ICESat2_Granule{:ATL03})`](@ref) と同様ですが、ATL08 データセットからの分類を使用します。ATL08 グラニュールが提供されていない場合は、[`convert`](@ref SpaceLiDAR.Base.convert) を使用して ATL03 名に基づいてそれを見つけようとします。
