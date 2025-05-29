```
xyzw2cube(fname::AbstractString; zcol::Int=4, datatype::DataType=Float32, proj4::String="", wkt::String="",
          epsg::Int=0, tit::String="", names::Vector{String}=String[], varnames::Vector{String}=String[])
```

または

```
xyzw2cube(D::GMTdataset; zcol::Int=4, datatype::DataType=Float32, tit::String="",
          names::Vector{String}=String[], varnames::Vector{String}=String[])
```

キューブを含むデータテーブルをGMTgridキューブに変換します。入力データは完全に埋められた3Dマトリックスを含む必要があり、データのレイアウトはファイル分析から推測されます（失敗した場合は...悪いチャンスです）。

### パラメータ

  * `fname`: テキスト形式のキューブのファイル名
  * `datatype`: データが保存されるデータ型。デフォルトはFloat32です。
  * `tit`: このキューブを説明するためのタイトル文字列。
  * `proj4`: データセットSRSのためのproj4文字列。
  * `wkt`: WKT SRSとして与えられた投影。
  * `epsg`: `proj`と同じですが、EPSGコードを使用します。
  * `names`: 各レイヤーの説明を提供するために使用されます（GDAL関数を使用する際にファイルに保存されます）。
  * `varnames`: キューブ内の変数の名前を持つ文字列ベクター。デフォルトでは、列名から取得します（利用可能な場合）。例: `varnames=["lon", "lat", "depth", "temp"]`。
  * `zcol`: z値が保存されている列番号。デフォルトは4です。データセットに4列以上があり、最後の列の1つをz値として使用したい場合は、より高い番号を使用してください。

### 戻り値

GMTgridキューブオブジェクト。
