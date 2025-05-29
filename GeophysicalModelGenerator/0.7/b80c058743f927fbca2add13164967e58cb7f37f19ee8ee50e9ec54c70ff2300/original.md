```
extract_subvolume(V::GeoData; Interpolate=false, Lon_level=nothing, Lat_level=nothing, Depth_level=nothing, dims=(50,50,50))
```

Extract or "cuts-out" a piece of a 2D or 3D GeoData set, defined by `Lon`, `Lat` and `Depth` coordinates.

This is useful if you are only interested in a part of a much bigger larger data set.

  * `Lon_level`,`Lat_level` and `Depth_level` should be tuples that indicate `(minimum_value, maximum_value)` along the respective direction. If not specified we use the full range.
  * By default, `Interpolate=false` and we find the closest indices within the data set (so your new data set will not go exactly from minimum to maximum).
  * Alternatively, if `Interpolate=true` we interpolate the data onto a new grid that has dimensions `dims`. This can be useful to compare data sets that are originally given in different resolutions.

# 3D Example with no interpolation:

```julia-repl
julia> Lon,Lat,Depth   =   lonlatdepth_grid(10:20,30:40,(-300:25:0)km);
julia> Data            =   Depth*2;                # some data
julia> Vx,Vy,Vz        =   ustrip(Data*3),ustrip(Data*4),ustrip(Data*5);
julia> Data_set3D      =   GeoData(Lon,Lat,Depth,(Depthdata=Data,LonData=Lon, Velocity=(Vx,Vy,Vz)))
GeoData
  size  : (11, 11, 13)
  lon   ϵ [ 10.0 : 20.0]
  lat   ϵ [ 30.0 : 40.0]
  depth ϵ [ -300.0 km : 0.0 km]
  fields: (:Depthdata, :LonData, :Velocity)
julia> Data_extracted = extract_subvolume(Data_set3D,Lon_level=(10,12),Lat_level=(35,40))
GeoData
  size  : (3, 6, 13)
  lon   ϵ [ 10.0 : 12.0]
  lat   ϵ [ 35.0 : 40.0]
  depth ϵ [ -300.0 km : 0.0 km]
  fields: (:Depthdata, :LonData, :Velocity)
```

By default it extracts the data points closest to the area defined by Lon*level/Lat*level/Depth_level.

# 3D Example with interpolation:

Alternatively, you can also interpolate the data onto a new grid:

```julia
julia> Data_extracted = extract_subvolume(Data_set3D,Lon_level=(10,12),Lat_level=(35,40), Interpolate=true, dims=(50,51,52))
GeoData
  size  : (50, 51, 52)
  lon   ϵ [ 10.0 : 12.0]
  lat   ϵ [ 35.0 : 40.0]
  depth ϵ [ -300.0 km : 0.0 km]
  fields: (:Depthdata, :LonData, :Velocity)
```
