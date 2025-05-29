cross*section*surface(Surface::GeoData; dims=(100,), Interpolate=false, Depth*level=nothing; Lat*level=nothing; Lon_level=nothing; Start=nothing, End=nothing )

サーフェス (2D) `GeoData` オブジェクトを通る断面を作成します。

  * 断面は、`Depth_level` が指定されている場合、水平（指定された深さでの地図ビュー）にすることができます。
  * また、`Lon_level` または `Lat_level` を指定することで垂直にすることもできます（固定の経度/緯度の場合）、または両方の `Start=(lon,lat)` と `End=(lon,lat)` ポイントを定義することによっても可能です。開始点と終了点は km で表されます！
  * 重要: 抽出されるサーフェスは、グリッド化された GeoData オブジェクトとして与えられる必要があります。定義されていない場所には NaN が含まれる場合があります。定義されたサーフェスの外にあるポイントはすべて NaN と見なされます。

# 例:

```julia-repl
julia> Lon,Lat,Depth   =   lonlatdepth_grid(10:20,30:40,-50km);
julia> Data            =   Depth*2;                # 一部のデータ
julia> Vx,Vy,Vz        =   ustrip(Data*3),ustrip(Data*4),ustrip(Data*5);
julia> Data_set2D      =   GeoData(Lon,Lat,Depth,(Depth=Depth,));
julia> Data_cross      =   cross_section_surface(Data_set2D, Lat_level =15)
GeoData
  size      : (100,)
  lon       ϵ [ 10.0 : 20.0]
  lat       ϵ [ 15.0 : 15.0]
  depth     ϵ [ NaN : NaN]
  fields    : (:Depth,)
  attributes: ["note"]
```
