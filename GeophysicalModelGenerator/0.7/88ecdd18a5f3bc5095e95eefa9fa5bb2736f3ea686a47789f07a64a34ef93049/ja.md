```
UTMData(EW::Any, NS:Any, depth::GeoUnit, UTMZone::Int, NorthernHemisphere=true, fields::NamedTuple)
```

UTM座標（東西）、（南北）および深さ情報を持つ1つまたは複数のフィールドを保持するデータ構造です。

  * `depth`はメートル、キロメートルの単位を持つか、単位なしであることができます。UTMZは通常メートルであるため、メートルに変換されます。
  * `fields`は理想的には各フィールドの名前を指定できるNamedTupleであるべきです。
  * 1つの配列のみを渡す場合、デフォルト名のNamedTupleに変換します。
  * 単一のフィールドは`(DataFieldName=Data,)`のように追加する必要があります（最後にカンマを忘れないでください）。
  * 複数のフィールドも追加できます。
  * Paraviewでベクトルフィールドを表示したい場合は、タプルとして追加します: `(Velocity=(Veast,Vnorth,Vup), Veast=Veast, Vnorth=Vnorth, Vup=Vup)`; これを`ParaviewData`構造に変換する際に自動的にベクトル変換を適用します。これにより矢印の大きさが変わるため、Paraviewでは`[Veast,Vnorth,Vup]`の成分は表示されなくなります。したがって、これらを別々のフィールドとして保存するのが良いアイデアです。
  * ただし、1つの例外があります: 3成分フィールドの名前が`colors`の場合、このフィールドはRGB色を含むと見なされるため、ベクトル変換は適用されません。
  * `Lat`、`Lon`、`Depth`は`Data`配列と同じサイズである必要があります。配列の順序は重要です。3D配列の場合、以下の例のように、最初の次元は`lon`、2番目の次元は`lat`、3番目の次元は`depth`（これはkmであるべきです）に対応すると仮定します。以下に例を示します。

# 例

```julia-repl
julia> ew          =   422123.0:100:433623.0
julia> ns          =   4.514137e6:100:4.523637e6
julia> depth       =   -5400:250:600
julia> EW,NS,Depth =   xyz_grid(ew, ns, depth);
julia> Data        =   ustrip.(Depth);
julia> Data_set    =   UTMData(EW,NS,Depth,33, true, (FakeData=Data,Data2=Data.+1.))
UTMData
  UTM zone : 33-33 North
    size    : (116, 96, 25)
    EW      ϵ [ 422123.0 : 433623.0]
    NS      ϵ [ 4.514137e6 : 4.523637e6]
    depth   ϵ [ -5400.0 m : 600.0 m]
    fields  : (:FakeData, :Data2)
  attributes: ["note"]
```

`UTMData`から`GeoData`に変換したい場合は、次のようにします。

```julia-repl
julia> Data_set1 =  convert(GeoData, Data_set)
GeoData
  size      : (116, 96, 25)
  lon       ϵ [ 14.075969111533457 : 14.213417764154963]
  lat       ϵ [ 40.77452227533946 : 40.86110443583479]
  depth     ϵ [ -5.4 km : 0.6 km]
  fields    : (:FakeData, :Data2)
  attributes: ["note"]
```

これにより、通常の方法でParaviewで視覚化することができます。

```julia-repl
julia> write_paraview(Data_set1, "Data_set1")
1-element Vector{String}:
 "Data_set1.vts"
```
