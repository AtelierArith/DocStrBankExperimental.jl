```
buildings_from_download(download_method::Symbol;
                        metadata::Bool=false,
                        download_format::Symbol=:osm,
                        save_to_file_location::Union{String,Nothing}=nothing,
                        download_kwargs...
                        )::Dict{Integer,Building}
```

OpenStreetMap API から `Building` オブジェクトをダウンロードして作成します。

# 引数

  * `download_method::Symbol`: ダウンロード方法、`:place_name`、`:bbox` または `:point` から選択します。
  * `metadata::Bool=false`: メタデータを返すには true に設定します。
  * `download_format::Symbol=:osm`: ダウンロード形式、`:osm`、`:xml` または `json` のいずれかです。
  * `save_to_file_location::Union{String,Nothing}=nothing`: ダウンロードしたデータをディスクに保存するファイルの場所を指定します。

# 必要なダウンロードキーワード引数

*`download_method=:place_name`*

  * `place_name::String`: Nominatim API に対する検索引数として使用される任意の場所名文字列。

*`download_method=:bbox`*

  * `minlat::AbstractFloat`: 左下のバウンディングボックスの緯度座標。
  * `minlon::AbstractFloat`: 左下のバウンディングボックスの経度座標。
  * `maxlat::AbstractFloat`: 右上のバウンディングボックスの緯度座標。
  * `maxlon::AbstractFloat`: 右上のバウンディングボックスの経度座標。

*`download_method=:point`*

  * `point::GeoLocation`: バウンディングボックスを描くための重心点。
  * `radius::Number`: 重心点から各バウンディングボックスの角までの距離 (km)。

# 戻り値

  * `Dict{Integer,Building}`: 建物の関係/ウェイ ID から `Building` オブジェクトへのマッピング。
