cross*section*surface(Surface::GeoData; dims=(100,), Interpolate=false, Depth*level=nothing; Lat*level=nothing; Lon_level=nothing; Start=nothing, End=nothing )

Creates a cross-section through a surface (2D) `GeoData` object.

  * Cross-sections can be horizontal (map view at a given depth), if `Depth_level` is specified
  * They can also be vertical, either by specifying `Lon_level` or `Lat_level` (for a fixed lon/lat), or by defining both `Start=(lon,lat)` & `End=(lon,lat)` points. Start and End points will be in km!
  * IMPORTANT: The surface to be extracted has to be given as a gridded GeoData object. It may also contain NaNs where it is not defined. Any points lying outside of the defined surface will be considered NaN.

# Example:

```julia-repl
julia> Lon,Lat,Depth   =   lonlatdepth_grid(10:20,30:40,-50km);
julia> Data            =   Depth*2;                # some data
julia> Vx,Vy,Vz        =   ustrip(Data*3),ustrip(Data*4),ustrip(Data*5);
julia> Data_set2D      =   GeoData(Lon,Lat,Depth,(Depth=Depth,));
julia> Data_cross      =   cross_section_surface(Data_set2D, Lat_level =15)
GeoData
  size      : (100,)
  lon       ϵ [ 10.0 : 20.0]
  lat       ϵ [ 15.0 : 15.0]
  depth     ϵ [ NaN : NaN]
  fields    : (:Depth,)
  attributes: ["note"]
```
