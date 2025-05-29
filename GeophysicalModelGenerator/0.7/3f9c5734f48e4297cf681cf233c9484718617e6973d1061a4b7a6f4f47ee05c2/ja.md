```
cross_section(DataSet::AbstractGeneralGrid; dims=(100,100), Interpolate=false, Depth_level=nothing, Lat_level=nothing, Lon_level=nothing, Start=nothing, End=nothing, Depth_extent=nothing, section_width=50km)
```

`GeoData`オブジェクトを通る断面を作成します。

  * 断面は、`Depth_level`が指定されている場合、水平（特定の深さでの地図ビュー）にすることができます。
  * また、`Lon_level`または`Lat_level`を指定することで垂直にすることもできます（固定の経度/緯度の場合）、または両方の`Start=(lon,lat)`と`End=(lon,lat)`ポイントを定義することによって。
  * 入力データの種類（体積、表面または点データ）に応じて、断面は異なる方法で作成されます：

1. 体積データ：データはデータセットから補間されるか、直接抽出されます。
2. 表面データ：表面データはデータセットから補間されるか、直接抽出されます。
3. 点データ：データは選択したプロファイルに投影されます。選択した距離内のデータのみ（デフォルトは50 km）が使用されます。

  * `Interpolate`は、データセットから単にデータを抽出したいのか（デフォルト）、それとも`dims`で指定された次元を持つ新しいグリッド上で線形補間したいのかを示します。注意：これは体積データおよび表面データセットにのみ適用されます。
  * 'section_width'は、点データがプロファイルに投影される最大距離を示します。

# 例：

```julia-repl
julia> Lon,Lat,Depth   =   lonlatdepth_grid(10:20,30:40,(-300:25:0)km);
julia> Data            =   Depth*2;                # 一部のデータ
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
