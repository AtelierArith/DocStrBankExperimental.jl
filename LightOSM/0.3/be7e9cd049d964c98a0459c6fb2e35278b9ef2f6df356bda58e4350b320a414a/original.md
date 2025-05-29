Representation of a geospatial coordinates.

# Fields

  * `lat::Float64`: Latitude.
  * `lon::Float64`: Longitude.
  * `alt::Float64`: Altitude.

# Constructors

```
GeoLocation(lat, lon)
GeoLocation(point::Vector{<:Real})
GeoLocation(point_vector::Vector{<:Vector{<:Real}})
GeoLocation(g::OSMGraph, ep::EdgePoint)
```
