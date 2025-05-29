```
ECEF{T} <: Coordinate{3}
```

地球中心地球固定座標（メートル単位）。

# 例

```jldoctest
julia> ECEF(LonLat(0,0))
ECEF{Float64}(6.378137e6, 0.0, 0.0)

julia> ECEF(LonLat(90,0))
ECEF{Float64}(0.0, 6.378137e6, 0.0)

julia> ECEF(LonLat(0,90))
ECEF{Float64}(0.0, 0.0, 6.356752314245179e6)
```
