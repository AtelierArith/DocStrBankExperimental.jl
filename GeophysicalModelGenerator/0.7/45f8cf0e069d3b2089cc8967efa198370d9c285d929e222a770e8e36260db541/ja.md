cross*section*volume(Volume::AbstractGeneralGrid; dims=(100,100), Interpolate=false, Depth*level=nothing; Lat*level=nothing; Lon*level=nothing; Start=nothing, End=nothing, Depth*extent=nothing )

ボリュメトリック（3D）`GeoData`オブジェクトを通る断面を作成します。

  * 断面は、`Depth_level`が指定されている場合、水平（特定の深さでの地図ビュー）にすることができます。
  * また、`Lon_level`または`Lat_level`（固定されたlon/lat）を指定することによって、または両方の`Start=(lon,lat)`と`End=(lon,lat)`ポイントを定義することによって、垂直にすることもできます。
  * `Start=(lon,lat)`と`End=(lon,lat)`の両方が与えられた場合、Depth*extent=(depth*min,depth_max)を提供することによってプロファイルの深さの範囲を提供することもできます。
  * `Interpolate`は、3Dボリュームからデータを単に抽出したいのか（デフォルト）、それとも`dims`で指定された次のグリッド上で線形補間を行いたいのかを示します。
  * `Depth_extent`は、垂直断面を補間したい深さの範囲を示すオプションのパラメータです。デフォルトは3Dデータセットの完全な垂直範囲です。

# 例:

```julia-repl
julia> Lon,Lat,Depth   =   lonlatdepth_grid(10:20,30:40,(-300:25:0)km);
julia> Data            =   Depth*2;                # 一部のデータ
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
