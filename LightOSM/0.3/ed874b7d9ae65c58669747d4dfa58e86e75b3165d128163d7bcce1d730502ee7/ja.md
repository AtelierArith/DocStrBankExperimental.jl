```
download_osm_buildings(download_method::Symbol;
                       metadata::Bool=false,
                       download_format::Symbol=:osm,
                       save_to_file_location::Union{String,Nothing}=nothing,
                       download_kwargs...
                       )::Union{XMLDocument,Dict{String,Any}}
```

OpenStreetMapの建物データを、地名、バウンディングボックス、またはセントロイドポイントを使ってクエリすることでダウンロードします。

# 引数

  * `download_method::Symbol`: ダウンロード方法。`:place_name`、`:bbox`、または`:point`から選択します。
  * `metadata::Bool=false`: メタデータを返す場合はtrueに設定します。
  * `download_format::Symbol=:osm`: ダウンロード形式。`:osm`、`:xml`、または`json`のいずれかです。
  * `save_to_file_location::Union{String,Nothing}=nothing`: ダウンロードしたデータをディスクに保存するファイルの場所を指定します。

# 必要なダウンロードKwargs

*`download_method=:place_name`*

  * `place_name::String`: Nominatim APIへの検索引数として使用される任意の地名文字列。

*`download_method=:bbox`*

  * `minlat::AbstractFloat`: 左下のバウンディングボックスの緯度座標。
  * `minlon::AbstractFloat`: 左下のバウンディングボックスの経度座標。
  * `maxlat::AbstractFloat`: 右上のバウンディングボックスの緯度座標。
  * `maxlon::AbstractFloat`: 右上のバウンディングボックスの経度座標。

*`download_method=:point`*

  * `point::GeoLocation`: バウンディングボックスを描くためのセントロイドポイント。
  * `radius::Number`: セントロイドポイントから各バウンディングボックスのコーナーまでの距離（km）。

# 戻り値

  * `Union{XMLDocument,Dict{String,Any}}`: ダウンロード方法に応じてXMLまたは辞書オブジェクトとして解析されたOpenStreetMapの建物データ。
