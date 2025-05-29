```
extract_subvolume(V::GeoData; Interpolate=false, Lon_level=nothing, Lat_level=nothing, Depth_level=nothing, dims=(50,50,50))
```

2Dまたは3DのGeoDataセットの一部を`Lon`、`Lat`、および`Depth`座標によって定義された「切り出し」または「抽出」します。

これは、はるかに大きなデータセットの一部にのみ興味がある場合に便利です。

  * `Lon_level`、`Lat_level`、および`Depth_level`は、それぞれの方向に沿った`(最小値、最大値)`を示すタプルである必要があります。指定されていない場合は、全範囲を使用します。
  * デフォルトでは、`Interpolate=false`であり、データセット内の最も近いインデックスを見つけます（したがって、新しいデータセットは最小から最大まで正確には移動しません）。
  * 代わりに、`Interpolate=true`の場合は、`dims`の次元を持つ新しいグリッドにデータを補間します。これは、元々異なる解像度で与えられたデータセットを比較するのに便利です。

# 補間なしの3D例：

```julia-repl
julia> Lon,Lat,Depth   =   lonlatdepth_grid(10:20,30:40,(-300:25:0)km);
julia> Data            =   Depth*2;                # 一部のデータ
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

デフォルトでは、Lon*level/Lat*level/Depth_levelによって定義された領域に最も近いデータポイントを抽出します。

# 補間ありの3D例：

代わりに、データを新しいグリッドに補間することもできます：

```julia
julia> Data_extracted = extract_subvolume(Data_set3D,Lon_level=(10,12),Lat_level=(35,40), Interpolate=true, dims=(50,51,52))
GeoData
  size  : (50, 51, 52)
  lon   ϵ [ 10.0 : 12.0]
  lat   ϵ [ 35.0 : 40.0]
  depth ϵ [ -300.0 km : 0.0 km]
  fields: (:Depthdata, :LonData, :Velocity)
```
