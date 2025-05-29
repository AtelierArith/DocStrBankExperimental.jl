```
graph_from_file(file_path::String;
                network_type::Symbol=:drive,
                weight_type::Symbol=:time,
                graph_type::Symbol=:static,
                precompute_dijkstra_states::Bool=false,
                largest_connected_component::Bool=true
                )::OSMGraph
```

ダウンロードしたOpenStreetMapネットワークデータファイルから`OSMGraph`オブジェクトを作成します。拡張子は`.json`、`.osm`、または`.xml`のいずれかでなければなりません。

# 引数

  * `file_path::String`: OpenStreetMapネットワークデータファイルの場所。
  * `network_type::Symbol=:drive`: ネットワークタイプフィルター。`:drive`、`:drive_service`、`:walk`、`:bike`、`:all`、`:all_private`、`:none`、`:rail`から選択します。`osm_data_object`をダウンロードする際に使用したネットワークタイプと一致する必要があります。
  * `weight_type::Symbol=:time`: グラフエッジの重みタイプ。`:distance`（km）、`:time`（時間）、`:lane_efficiency`（レーン数でスケーリングされた時間）から選択します。
  * `graph_type::Symbol=:static`: `Graphs.AbstractGraph`のタイプ。`:static`（StaticDiGraph）、`:light`（DiGraph）、`:simple_weighted`（SimpleWeightedDiGraph）、`:meta`（MetaDiGraph）から選択します。
  * `precompute_dijkstra_states::Bool=false`: グラフ内のすべてのソースノードに対してダイクストラの親状態を事前計算するにはtrueに設定します。*注意* これは時間がかかる場合があり、ノード数が多いグラフではメモリ制限のために不可能な場合があります。
  * `largest_connected_component::Bool=true`: ネットワーク内の最大の連結成分のみを保持するにはtrueに設定します。
  * `filter_network_type::Bool=true`: `network_type`フィルターと一致しないノードとエッジを除外するにはtrueに設定します。カスタムOverpassフィルターでダウンロードされたネットワークデータや、LightOSMで生成されていない場合に便利です。

# 戻り値

  * `OSMGraph`: OpenStreetMapのノード、ウェイ、リレーション、およびグラフ関連オブジェクトを格納するためのコンテナ。
