```
classify(granule::ICESat2_Granule{:ATL03}, atl08::Union{ICESat2_Granule{:ATL08},Nothing} = nothing, tracks = icesat2_tracks)
```

Like [`points(::ICESat2_Granule{:ATL03})`](@ref) but with the classification from the ATL08 dataset. If an ATL08 granule is not provided, we try to find it based on the ATL03 name using [`convert`](@ref SpaceLiDAR.Base.convert).
