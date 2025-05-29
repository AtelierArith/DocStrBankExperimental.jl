```
lonlat2bng(lon, lat) -> easting, northing
```

Transform from `lon`gitude and `lat`itude (degrees) in WGS84 into BNG `easting` and `northing` (m).

!!! note
    This function does not throw an error if `lon` and `lat` are at a point outside the bounds of the National Grid.  Therefore this function should be used with caution.


# Example

```jldoctest
julia> lon, lat = -3.183503, 55.954983;

julia> lonlat2bng(lon, lat)
(326200.06052230217, 674183.9198954724)

```
