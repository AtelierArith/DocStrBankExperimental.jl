```
extract_subvolume(V::CartData; Interpolate=false, X_level=nothing, Y_level=nothing, Z_level=nothing, dims=(50,50,50))
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

# 2D Example along a cross-section through 3D data:

```julia-repl
julia> X,Y,Z = xyz_grid(10:20,30:40,-300:25:0);
julia> Data = Z.*2
julia> Data_Int = Int64.(Data)
julia> DataSet_Cart = CartData(X,Y,Z,(Data=Data,Data_Int=Data_Int, Velocity=(X,Y,Z)))

julia> Data_cross = cross_section(DataSet_Cart, Start=(11.0,35), End=(19, 39.0))
CartData
    size    : (100, 100, 1)
    x       ϵ [ 11.0 : 19.0]
    y       ϵ [ 35.0 : 39.0]
    z       ϵ [ -300.0 : 0.0]
    fields  : (:Data, :Data_Int, :Velocity, :FlatCrossSection)
  attributes: ["note"]

julia> Data_extracted = extract_subvolume(Data_cross, X_level=(1,7), Z_level=(-200,-100))
  CartData
      size    : (50, 50, 1)
      x       ϵ [ 11.894427190999917 : 17.260990336999413]
      y       ϵ [ 35.44721359549995 : 38.130495168499706]
      z       ϵ [ -200.0 : -100.0]
      fields  : (:FlatCrossSection, :Data, :Data_Int, :Velocity)
    attributes: ["note"]
julia> typeof(Data_extracted.fields.Data_Int)
    Array{Int64, 3}
```
