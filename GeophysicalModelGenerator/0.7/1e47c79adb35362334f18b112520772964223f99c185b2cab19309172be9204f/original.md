```
above_surface(Data::GeoData, DataSurface::GeoData; above=true)
```

Returns a boolean array of size(Data.Lon), which is true for points that are above the surface DataSurface (or for points below if above=false).

This can be used, for example, to mask points above/below the Moho in a volumetric dataset or in a profile.

# Example

First we create a 3D data set and a 2D surface:

```julia-repl
julia> Lon,Lat,Depth   =   lonlatdepth_grid(10:20,30:40,(-300:25:0)km);
julia> Data            =   Depth*2;
julia> Data_set3D      =   GeoData(Lon,Lat,Depth,(Depthdata=Data,LonData=Lon))
GeoData
  size  : (11, 11, 13)
  lon   ϵ [ 10.0 : 20.0]
  lat   ϵ [ 30.0 : 40.0]
  depth ϵ [ -300.0 km : 0.0 km]
  fields: (:Depthdata, :LonData)
julia> Lon,Lat,Depth   =   lonlatdepth_grid(10:20,30:40,-40km);
julia> Data_Moho       =   GeoData(Lon,Lat,Depth+Lon*km, (MohoDepth=Depth,))
  GeoData
    size  : (11, 11, 1)
    lon   ϵ [ 10.0 : 20.0]
    lat   ϵ [ 30.0 : 40.0]
    depth ϵ [ -30.0 km : -20.0 km]
    fields: (:MohoDepth,)
```

Next, we intersect the surface with the data set:

```julia-repl
julia> Above       =   above_surface(Data_set3D, Data_Moho);
```

Now, `Above` is a boolean array that is true for points above the surface and false for points below and at the surface.
