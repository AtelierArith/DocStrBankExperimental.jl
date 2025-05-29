```
graph_from_download(download_method::Symbol;
                    network_type::Symbol=:drive,
                    metadata::Bool=false,
                    download_format::Symbol=:json,
                    save_to_file_location::Union{String,Nothing}=nothing,
                    weight_type::Symbol=:time,
                    graph_type::Symbol=:static,
                    precompute_dijkstra_states::Bool=false,
                    largest_connected_component::Bool=true,
                    download_kwargs...
                    )::OSMGraph
```

OpenStreetMapネットワークデータをダウンロードし、`OSMGraph`オブジェクトを作成します。

# 引数

  * `download_method::Symbol`: ダウンロード方法、`:place_name`、`:bbox`、または`:point`から選択します。
  * `network_type::Symbol=:drive`: ネットワークタイプフィルター、`:drive`、`:drive_service`、`:walk`、`:bike`、`:all`、`:all_private`、`:none`、`:rail`から選択します。
  * `metadata::Bool=false`: メタデータを返すにはtrueに設定します。
  * `download_format::Symbol=:json`: ダウンロード形式、`:osm`、`:xml`、またはjsonのいずれかです。
  * `save_to_file_location::Union{String,Nothing}=nothing`: ダウンロードしたデータをディスクに保存するファイルの場所を指定します。
  * `weight_type::Symbol=:time`: グラフエッジの重みタイプ、`:distance`（km）、`:time`（時間）、`:lane_efficiency`（レーン数でスケーリングされた時間）から選択します。
  * `graph_type::Symbol=:static`: `Graphs.AbstractGraph`のタイプ、`:static`（StaticDiGraph）、`:light`（DiGraph）、`:simple_weighted`（SimpleWeightedDiGraph）、`:meta`（MetaDiGraph）から選択します。
  * `precompute_dijkstra_states::Bool=false`: グラフ内のすべてのソースノードのためにダイクストラ親状態を事前計算するにはtrueに設定します。*注意* これは時間がかかる場合があり、メモリ制限のためにノード数が多いグラフでは不可能な場合があります。
  * `largest_connected_component::Bool=true`: ネットワーク内の最大の連結成分のみを保持するにはtrueに設定します。
  * `filter_network_type::Bool=true`: ダウンロード後に`network_type`フィルターに一致しないノードとエッジをフィルタリングするにはtrueに設定します。これは`download_method=:custom_filters`と一緒に使用することをお勧めします。

# 各ダウンロード方法に必要なKwargs

*`download_method=:place_name`*

  * `place_name::String`: Nominatim APIへの検索引数として使用される任意の場所名文字列。

*`download_method=:bbox`*

  * `minlat::AbstractFloat`: 左下のバウンディングボックスの緯度座標。
  * `minlon::AbstractFloat`: 左下のバウンディングボックスの経度座標。
  * `maxlat::AbstractFloat`: 右上のバウンディングボックスの緯度座標。
  * `maxlon::AbstractFloat`: 右上のバウンディングボックスの経度座標。

*`download_method=:point`*

  * `point::GeoLocation`: バウンディングボックスを描くための重心点。
  * `radius::Number`: 重心点から各バウンディングボックスの角までの距離（km）。

*`download_method=:polygon`*

  * `polygon::AbstractVector`: 経度-緯度ペアのベクター。

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

  * `OSMGraph`: OpenStreetMapノード、ウェイ、リレーション、およびグラフ関連オブジェクトを格納するためのコンテナ。
