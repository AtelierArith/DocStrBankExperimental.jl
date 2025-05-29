```
graph_from_object(osm_data_object::Union{XMLDocument,Dict};
                  network_type::Symbol=:drive,
                  weight_type::Symbol=:time,
                  graph_type::Symbol=:static,
                  precompute_dijkstra_states::Bool=false,
                  largest_connected_component::Bool=true
                  )::OSMGraph
```

OpenStreetMapネットワークデータから`OSMGraph`オブジェクトを作成します。`download_osm_network`と一緒に使用します。

# 引数

  * `osm_data_object::Union{XMLDocument,Dict}`: ダウンロード方法に応じて`XMLDocument`または`Dict`オブジェクトとして解析されたOpenStreetMapネットワークデータ。*注意* `Dict`を渡すと、オブジェクトは不足しているタグ情報を追加するように修正されます。
  * `network_type::Symbol=:drive`: ネットワークタイプフィルター。`:drive`、`:drive_service`、`:walk`、`:bike`、`:all`、`:all_private`、`:none`、`:rail`から選択し、`osm_data_object`のダウンロードに使用されたネットワークタイプと一致する必要があります。
  * `weight_type::Symbol=:time`: グラフエッジの重みタイプ。`:distance`（km）、`:time`（時間）、`:lane_efficiency`（レーン数でスケーリングされた時間）から選択します。
  * `graph_type::Symbol=:static`: `Graphs.AbstractGraph`のタイプ。`:static`（`StaticDiGraph`）、`:light`（`DiGraph`）、`:simple_weighted`（`SimpleWeightedDiGraph`）、`:meta`（`MetaDiGraph`）から選択します。
  * `precompute_dijkstra_states::Bool=false`: グラフ内のすべてのソースノードに対してダイクストラの親状態を事前計算するにはtrueに設定します。*注意* これは時間がかかる場合があり、ノード数が多いグラフではメモリ制限のために不可能な場合があります。
  * `largest_connected_component::Bool=true`: ネットワーク内の最大の連結成分のみを保持するにはtrueに設定します。
  * `filter_network_type::Bool=true`: `network_type`フィルターと一致しないノードとエッジをフィルタリングするにはtrueに設定します。カスタムOverpassフィルターでダウンロードされたネットワークデータや、LightOSMで生成されていない場合に便利です。

# 戻り値

  * `OSMGraph`: OpenStreetMapのノード、ウェイ、リレーション、およびグラフ関連オブジェクトを格納するためのコンテナ。
