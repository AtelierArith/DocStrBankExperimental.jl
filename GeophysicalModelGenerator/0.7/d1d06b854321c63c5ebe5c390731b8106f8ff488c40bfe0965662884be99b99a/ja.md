```
pvd = write_paraview(DataSet::ParaviewData, filename="test"; PointsData=false, pvd=nothing, time=nothing, directory=nothing, verbose=true)
```

`Geodata`を持つ構造体をparaview（またはVTK）ファイルに書き込みます。非構造化ポイント（例：地震データ）がある場合は、`PointsData=true`に設定してください。Paraviewでムービーを作成したい場合、このムービーのタイムステップであるため、`time`と`pvd`も渡す必要があります。

# 例 1: 3Dボリュームの書き込み

```julia-repl
julia> Lon,Lat,Depth   =   lonlatdepth_grid(10:20,30:40,(-300:25:0)km);
julia> Data_set        =   GeoData(Lat,Lon,Depth,(Depthdata=Depth,LonData=Lon))  
julia> write_paraview(Data_set, "test_depth3D")
```

# 例 2: 指定深度での水平スライス

```julia-repl
julia> Lon,Lat,Depth  =   lonlatdepth_grid(10:20,30:40,10km);
julia> Data_set       =   GeoData(Lat,Lon,Depth,(Topography=Depth,))  
julia> write_paraview(Data_set, "test")
```

# 例 3: 地形を含むケース

```julia-repl
julia> Lon,Lat,Depth    =   lonlatdepth_grid(10:20,30:40,10km);
julia> Depth[2:4,2:4,1] .=  25km     
julia> Data_set         =   GeoData(Lat,Lon,Depth,(Topography=Depth,))  
julia> write_paraview(Data_set, "test2")
```

# 例 4: プロファイル

```julia-repl
julia> Lon,Lat,Depth  =   lonlatdepth_grid(10:20,35,(-300:25:0)km);
julia> Data_set       =   GeoData(Lat,Lon,Depth,(DataSet=Depth,Depth=Depth))  
julia> write_paraview(Data_set, "test")
```

# 例 5: 速度ベクトル

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

# 例 6: 非接続ポイント（例：地震の位置）

これらのポイントは1Dベクトルである必要があります。

```julia-repl
julia> Lon,Lat,Depth  =   lonlatdepth_grid(10:5:20,35:2:40,(-300:50:0)km);
julia> Lon=Lon[:]; Lat=Lat[:]; Depth=Depth[:];
julia> Data_set       =   GeoData(Lat,Lon,Depth,(DataSet=Depth[:],Depth=Depth*10));  
julia> write_paraview(Data_set, "test_Points", PointsData=true)
```
