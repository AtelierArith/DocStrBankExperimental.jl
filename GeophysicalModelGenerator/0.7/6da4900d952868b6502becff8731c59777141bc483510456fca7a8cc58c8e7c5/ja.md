```
extract_subvolume(V::CartData; Interpolate=false, X_level=nothing, Y_level=nothing, Z_level=nothing, dims=(50,50,50))
```

2Dまたは3DのGeoDataセットの一部を`Lon`、`Lat`、`Depth`座標で定義された領域から「抽出」または「切り出す」ための関数です。

これは、はるかに大きなデータセットの一部にのみ興味がある場合に便利です。

  * `Lon_level`、`Lat_level`、および`Depth_level`は、それぞれの方向に沿った`(最小値, 最大値)`を示すタプルである必要があります。指定されていない場合は、全範囲を使用します。
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

デフォルトでは、Lon*level/Lat*level/Depth_levelで定義された領域に最も近いデータポイントを抽出します。

# 3Dデータを通る断面に沿った2D例：

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
