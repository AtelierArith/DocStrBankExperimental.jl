```julia
minarcdistance(latᵢ,lonᵢ,lat,lon)
```

Return the smallest non-`NaN` arcdistance (i.e. distance on a sphere in arc degrees) between a given point (`latᵢ[i]`,`lonᵢ[i]`) and any point in (`lat`,`lon`) for each `i` in `eachindex(latᵢ, lonᵢ)`.

Latitude and Longitude should be specified in decimal degrees
