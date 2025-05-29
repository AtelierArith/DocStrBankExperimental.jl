```
function cross_section_points(P::GeoData; Depth_level=nothing, Lat_level=nothing, Lon_level=nothing, Start=nothing, End=nothing, section_width=50 )
```

Creates a projection of separate points (saved as a GeoData object) onto a chosen plane. Only points with a maximum distance of section_width are taken into account
