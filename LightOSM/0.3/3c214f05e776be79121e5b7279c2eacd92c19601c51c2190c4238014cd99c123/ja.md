```
download_osm_network(download_method::Symbol;
                     network_type::Symbol=:drive,
                     metadata::Bool=false,
                     download_format::Symbol=:json,
                     save_to_file_location::Union{String,Nothing}=nothing,
                     download_kwargs...
                     )::Union{XMLDocument,Dict{String,Any}}
```

OpenStreetMapネットワークを、地名、バウンディングボックス、またはセントロイドポイントでクエリしてダウンロードします。

# 引数

  * `download_method::Symbol`: ダウンロード方法、`:place_name`、`:bbox`、または`:point`から選択します。
  * `network_type::Symbol=:drive`: ネットワークタイプフィルター、`:drive`、`:drive_service`、`:walk`、`:bike`、`:all`、`:all_private`、`:none`、`:rail`から選択します。
  * `metadata::Bool=false`: メタデータを返すにはtrueに設定します。
  * `download_format::Symbol=:json`: ダウンロード形式、`:osm`、`:xml`、またはjsonのいずれかです。
  * `save_to_file_location::Union{String,Nothing}=nothing`: ダウンロードしたデータをディスクに保存するファイルの場所を指定します。

# 各ダウンロード方法に必要なKwargs

*`download_method=:place_name`*

  * `place_name::String`: Nominatim APIへの検索引数として使用される任意の地名文字列。

*`download_method=:bbox`*

  * `minlat::AbstractFloat`: 左下のバウンディングボックスの緯度座標。
  * `minlon::AbstractFloat`: 左下のバウンディングボックスの経度座標。
  * `maxlat::AbstractFloat`: 右上のバウンディングボックスの緯度座標。
  * `maxlon::AbstractFloat`: 右上のバウンディングボックスの経度座標。

*`download_method=:point`*

  * `point::GeoLocation`: バウンディングボックスを描くためのセントロイドポイント。
  * `radius::Number`: セントロイドポイントから各バウンディングボックスの角までの距離（km）。

*`download_method=:polygon`*

  * `polygon::AbstractVector`: 経度-緯度ペアのベクター。

*`download_method=:custom_filters`*

  * `custom_filters::String`: クエリのフィルター、例：ポリゴンフィルター、高速道路のみ、信号機のみなど。
  * `metadata::Bool=false`: メタデータを返すにはtrueに設定します。
  * `download_format::Symbol=:json`: ダウンロード形式、`:osm`、`:xml`、またはjsonのいずれかです。
  * `bbox::Union{Vector{AbstractFloat},Nothing}=nothing`: オプションのバウンディングボックスフィルター。

# ネットワークタイプ

  * `:drive`: プライベートおよびサービス道路を除く高速道路。
  * `:drive_service`: プライベートおよびサービス道路を含む高速道路。
  * `:walk`: 歩道のみ。
  * `:bike`: 自転車道のみ。
  * `:all`: プライベート道路を除くすべての高速道路、歩道、自転車道。
  * `:all_private`: プライベート道路を含むすべての高速道路、歩道、自転車道。
  * `:none`: ネットワークフィルターなし。
  * `:rail`: 提案されたものとプラットフォームを除く鉄道。

# 戻り値

  * `Union{XMLDocument,Dict{String,Any}}`: ダウンロード方法に応じてXMLまたは辞書オブジェクトとして解析されたOpenStreetMapネットワークデータ。
