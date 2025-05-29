```
quadkey(lon::Real, lat::Real, zoom::Int; bounds=false, geog=true)
```

  * `bounds`: If true, returns the bounding box of the tile, otherwise returns the tile XYZ coordinates and the quadtree string.
  * `geog`: return the bounding box in geographic coordinates. If false, returns the bounding box in spherical Mercator coordinates

Returns the x,y,z & the quadtree string or the bounds

### Examples

```jldoctest
julia> quadkey(-9,39, 8)
([121, 97, 8], ["03311003";;])
```

```jldoctest
julia> quadkey(-9,39, 8, bounds=true)
2×2 Matrix{Float64}:
 -9.84375  38.8226
 -8.4375   39.9097
```

The form bellow returns the quadtree representation of the XYZ tile or the bounds coordinates in geographic coordinates

```
quadkey(xyz::VecOrMat{<:Int}; bounds=true, geog=true)
```

### Examples

```jldoctest
julia> quadkey([121, 97, 8], bounds=false)
"03311003"
```
