```
cross_section(DataSet::AbstractGeneralGrid; dims=(100,100), Interpolate=false, Depth_level=nothing, Lat_level=nothing, Lon_level=nothing, Start=nothing, End=nothing, Depth_extent=nothing, section_width=50km)
```

Creates a cross-section through a `GeoData` object.

  * Cross-sections can be horizontal (map view at a given depth), if `Depth_level` is specified
  * They can also be vertical, either by specifying `Lon_level` or `Lat_level` (for a fixed lon/lat), or by defining both `Start=(lon,lat)` & `End=(lon,lat)` points.
  * Depending on the type of input data (volume, surface or point data), cross sections will be created in a different manner:

1. Volume data: data will be interpolated or directly extracted from the data set.
2. Surface data: surface data will be interpolated or directly extracted from the data set
3. Point data: data will be projected to the chosen profile. Only data within a chosen distance (default is 50 km) will be used

  * `Interpolate` indicates whether we want to simply extract the data from the data set (default) or whether we want to linearly interpolate it on a new grid, which has dimensions as specified in `dims` NOTE: THIS ONLY APPLIES TO VOLUMETRIC AND SURFACE DATA SETS
  * 'section_width' indicates the maximal distance within which point data will be projected to the profile

# Example:

```julia-repl
julia> Lon,Lat,Depth   =   lonlatdepth_grid(10:20,30:40,(-300:25:0)km);
julia> Data            =   Depth*2;                # some data
julia> Vx,Vy,Vz        =   ustrip(Data*3),ustrip(Data*4),ustrip(Data*5);
julia> Data_set3D      =   GeoData(Lon,Lat,Depth,(Depthdata=Data,LonData=Lon, Velocity=(Vx,Vy,Vz)));
julia> Data_cross      =   cross_section(Data_set3D, Depth_level=-100km)
GeoData
  size  : (11, 11, 1)
  lon   ϵ [ 10.0 : 20.0]
  lat   ϵ [ 30.0 : 40.0]
  depth ϵ [ -100.0 km : -100.0 km]
  fields: (:Depthdata, :LonData, :Velocity)
```
