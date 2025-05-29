```
above_surface(Data::GeoData, DataSurface::GeoData; above=true)
```

データサーフェス DataSurface の上にある点に対して true となる、サイズ(Data.Lon) のブール配列を返します（また、above=false の場合は下にある点に対して true となります）。

これは、例えば、ボリュメトリックデータセットやプロファイルにおいて、モホの上/下にある点をマスクするために使用できます。

# 例

まず、3Dデータセットと2Dサーフェスを作成します：

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

次に、データセットとサーフェスを交差させます：

```julia-repl
julia> Above       =   above_surface(Data_set3D, Data_Moho);
```

これで、`Above` はサーフェスの上にある点に対して true、下またはサーフェス上にある点に対して false となるブール配列です。
