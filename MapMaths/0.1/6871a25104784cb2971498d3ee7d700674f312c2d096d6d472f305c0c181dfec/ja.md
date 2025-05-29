```
WebMercator{T} <: Coordinate{2,T}
```

WebMercator座標は、次の同一性を持つようにシフトおよびスケールされています。

```jldoctest; output = false
julia> @assert WebMercator(LonLat( 0, 0 ))[] == (0, 0)

julia> @assert WMX(Lon(180))[] == +1

julia> @assert WMY(Lat(90))[] == +Inf
```
