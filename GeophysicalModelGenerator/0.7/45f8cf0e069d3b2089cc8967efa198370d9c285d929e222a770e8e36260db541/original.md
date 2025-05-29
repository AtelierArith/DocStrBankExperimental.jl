cross*section*volume(Volume::AbstractGeneralGrid; dims=(100,100), Interpolate=false, Depth*level=nothing; Lat*level=nothing; Lon*level=nothing; Start=nothing, End=nothing, Depth*extent=nothing )

Creates a cross-section through a volumetric (3D) `GeoData` object.

  * Cross-sections can be horizontal (map view at a given depth), if `Depth_level` is specified
  * They can also be vertical, either by specifying `Lon_level` or `Lat_level` (for a fixed lon/lat), or by defining both `Start=(lon,lat)` & `End=(lon,lat)` points.
  * When both `Start=(lon,lat)` & `End=(lon,lat)` are given, one can also provide a the depth extent of the profile by providing Depth*extent=(depth*min,depth_max)
  * `Interpolate` indicates whether we want to simply extract the data from the 3D volume (default) or whether we want to linearly interpolate it on a new grid, which has dimensions as specified in `dims`
  * `Depth_extent` is an optional parameter that can indicate the depth extent over which you want to interpolate the vertical cross-section. Default is the full vertical extent of the 3D dataset

# Example:

```julia-repl
julia> Lon,Lat,Depth   =   lonlatdepth_grid(10:20,30:40,(-300:25:0)km);
julia> Data            =   Depth*2;                # some data
julia> Vx,Vy,Vz        =   ustrip(Data*3),ustrip(Data*4),ustrip(Data*5);
julia> Data_set3D      =   GeoData(Lon,Lat,Depth,(Depthdata=Data,LonData=Lon, Velocity=(Vx,Vy,Vz)));
julia> Data_cross      =   cross_section_volume(Data_set3D, Depth_level=-100km)
GeoData
  size  : (11, 11, 1)
  lon   ϵ [ 10.0 : 20.0]
  lat   ϵ [ 30.0 : 40.0]
  depth ϵ [ -100.0 km : -100.0 km]
  fields: (:Depthdata, :LonData, :Velocity)
```
