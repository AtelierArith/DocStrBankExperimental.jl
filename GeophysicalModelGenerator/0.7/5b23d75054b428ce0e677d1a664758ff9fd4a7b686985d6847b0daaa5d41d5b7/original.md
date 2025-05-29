```
GeoData(lld::Tuple{Array,Array,Array})
```

This creates a `GeoData` struct if you have a Tuple with 3D coordinates as input.

# Example

```julia
julia> data = GeoData(lonlatdepth_grid(-10:10,-5:5,0))
GeoData 
  size      : (21, 11, 1)
  lon       ϵ [ -10.0 : 10.0]
  lat       ϵ [ -5.0 : 5.0]
  depth     ϵ [ 0.0 : 0.0]
  fields    : (:Z,)
```
