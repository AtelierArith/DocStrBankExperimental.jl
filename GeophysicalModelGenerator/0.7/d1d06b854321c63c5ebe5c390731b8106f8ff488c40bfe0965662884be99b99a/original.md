```
pvd = write_paraview(DataSet::ParaviewData, filename="test"; PointsData=false, pvd=nothing, time=nothing, directory=nothing, verbose=true)
```

Writes a structure with `Geodata` to a paraview (or VTK) file. If you have unstructured points (e.g., earthquake data), set `PointsData=true`. In case you want to create a movie in Paraview, and this is a timestep of that movie you also have to pass `time` and `pvd`

# Example 1: Write a 3D volume

```julia-repl
julia> Lon,Lat,Depth   =   lonlatdepth_grid(10:20,30:40,(-300:25:0)km);
julia> Data_set        =   GeoData(Lat,Lon,Depth,(Depthdata=Depth,LonData=Lon))  
julia> write_paraview(Data_set, "test_depth3D")
```

# Example 2: Horizontal slice @ given depth

```julia-repl
julia> Lon,Lat,Depth  =   lonlatdepth_grid(10:20,30:40,10km);
julia> Data_set       =   GeoData(Lat,Lon,Depth,(Topography=Depth,))  
julia> write_paraview(Data_set, "test")
```

# Example 3: Case with topography

```julia-repl
julia> Lon,Lat,Depth    =   lonlatdepth_grid(10:20,30:40,10km);
julia> Depth[2:4,2:4,1] .=  25km     
julia> Data_set         =   GeoData(Lat,Lon,Depth,(Topography=Depth,))  
julia> write_paraview(Data_set, "test2")
```

# Example 4: Profile

```julia-repl
julia> Lon,Lat,Depth  =   lonlatdepth_grid(10:20,35,(-300:25:0)km);
julia> Data_set       =   GeoData(Lat,Lon,Depth,(DataSet=Depth,Depth=Depth))  
julia> write_paraview(Data_set, "test")
```

# Example 5: Velocity vectors

```julia-repl
julia> Lon,Lat,Depth  =   lonlatdepth_grid(10:20,30:40,10km);
julia> Ve, Vn, Vz     =   ones(size(Depth)), ones(size(Depth))*0.5, zeros(size(Depth));
julia> Data_set       =   GeoData(Lat,Lon,Depth,(DataSet=Depth, Velocity=(Ve,Vn,Vz)))
GeoData 
  size  : (11, 11, 1)
  lon   ϵ [ 30.0 - 40.0]
  lat   ϵ [ 10.0 - 20.0]
  depth ϵ [ 10.0 km - 10.0 km]
  fields: (:DataSet, :Velocity)  
julia> write_paraview(Data_set, "test_Velocity")
```

# Example 6: Unconnected points (e.g., earthquake locations)

Note that these points should be 1D vectors.

```julia-repl
julia> Lon,Lat,Depth  =   lonlatdepth_grid(10:5:20,35:2:40,(-300:50:0)km);
julia> Lon=Lon[:]; Lat=Lat[:]; Depth=Depth[:];
julia> Data_set       =   GeoData(Lat,Lon,Depth,(DataSet=Depth[:],Depth=Depth*10));  
julia> write_paraview(Data_set, "test_Points", PointsData=true)
```
