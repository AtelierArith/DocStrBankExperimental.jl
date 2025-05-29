```
GeoData(lon::Any, lat:Any, depth::GeoUnit, fields::NamedTuple)
```

経度、緯度、深度情報を持つ1つまたは複数のフィールドを保持するデータ構造です。

  * `depth`はメートル、キロメートルの単位を持つか、単位なしであることができ、kmに変換されます。
  * `fields`は理想的には各フィールドの名前を指定できるNamedTupleであるべきです。
  * 1つの配列のみを渡した場合、デフォルト名のNamedTupleに変換されます。
  * 単一のフィールドは`(DataFieldName=Data,)`のように追加する必要があります（最後のカンマを忘れないでください）。
  * 複数のフィールドも追加できます。`lon`、`lat`、`depth`はすべて`fields`と同じサイズである必要があります。
  * Paraviewでベクトルフィールドを表示したい場合は、タプルとして追加します: `(Velocity=(Veast,Vnorth,Vup), Veast=Veast, Vnorth=Vnorth, Vup=Vup)`; これを`ParaviewData`構造に変換する際に自動的にベクトル変換が適用され、Paraview出力が生成されます。これにより矢印の大きさが変わるため、Paraviewでは`[Veast,Vnorth,Vup]`の成分は表示されなくなります。したがって、別々のフィールドとして保存するのが良いアイデアです。
  * ただし、1つの例外があります: 3成分フィールドの名前が`colors`の場合、このフィールドはRGB色を含むと見なされるため、ベクトル変換は適用されません。
  * `Lat`、`Lon`、`Depth`は`Data`配列と同じサイズである必要があります。配列の順序は重要です。3D配列の場合、以下の例のように、最初の次元が`lon`、2番目の次元が`lat`、3番目の次元が`depth`（km単位）に対応すると仮定します。以下に例を示します。

# 例

```julia-repl
julia> Lat         =   1.0:3:10.0;
julia> Lon         =   11.0:4:20.0;
julia> Depth       =   (-20:5:-10)*km;
julia> Lon3D,Lat3D,Depth3D = lonlatdepth_grid(Lon, Lat, Depth);
julia> Lon3D
3×4×3 Array{Float64, 3}:
[:, :, 1] =
 11.0  11.0  11.0  11.0
 15.0  15.0  15.0  15.0
 19.0  19.0  19.0  19.0

[:, :, 2] =
 11.0  11.0  11.0  11.0
 15.0  15.0  15.0  15.0
 19.0  19.0  19.0  19.0

[:, :, 3] =
 11.0  11.0  11.0  11.0
 15.0  15.0  15.0  15.0
 19.0  19.0  19.0  19.0
julia> Lat3D
 3×4×3 Array{Float64, 3}:
 [:, :, 1] =
  1.0  4.0  7.0  10.0
  1.0  4.0  7.0  10.0
  1.0  4.0  7.0  10.0

 [:, :, 2] =
  1.0  4.0  7.0  10.0
  1.0  4.0  7.0  10.0
  1.0  4.0  7.0  10.0

 [:, :, 3] =
  1.0  4.0  7.0  10.0
  1.0  4.0  7.0  10.0
  1.0  4.0  7.0  10.0
julia> Depth3D
  3×4×3 Array{Unitful.Quantity{Float64, 𝐋, Unitful.FreeUnits{(km,), 𝐋, nothing}}, 3}:
  [:, :, 1] =
   -20.0 km  -20.0 km  -20.0 km  -20.0 km
   -20.0 km  -20.0 km  -20.0 km  -20.0 km
   -20.0 km  -20.0 km  -20.0 km  -20.0 km

  [:, :, 2] =
   -15.0 km  -15.0 km  -15.0 km  -15.0 km
   -15.0 km  -15.0 km  -15.0 km  -15.0 km
   -15.0 km  -15.0 km  -15.0 km  -15.0 km

  [:, :, 3] =
   -10.0 km  -10.0 km  -10.0 km  -10.0 km
   -10.0 km  -10.0 km  -10.0 km  -10.0 km
   -10.0 km  -10.0 km  -10.0 km  -10.0 km
julia> Data        =   zeros(size(Lon3D));
julia> Data_set    =   GeophysicalModelGenerator.GeoData(Lon3D,Lat3D,Depth3D,(DataFieldName=Data,))
GeoData
  size      : (3, 4, 3)
  lon       ϵ [ 11.0 : 19.0]
  lat       ϵ [ 1.0 : 10.0]
  depth     ϵ [ -20.0 km : -10.0 km]
  fields    : (:DataFieldName,)
  attributes: ["note"]
```
