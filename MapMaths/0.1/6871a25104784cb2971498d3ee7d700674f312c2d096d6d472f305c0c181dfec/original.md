```
WebMercator{T} <: Coordinate{2,T}
```

WebMercator coordinates, shifted and scaled such that we have the following identities.

```jldoctest; output = false
julia> @assert WebMercator(LonLat( 0, 0 ))[] == (0, 0)

julia> @assert WMX(Lon(180))[] == +1

julia> @assert WMY(Lat(90))[] == +Inf
```
