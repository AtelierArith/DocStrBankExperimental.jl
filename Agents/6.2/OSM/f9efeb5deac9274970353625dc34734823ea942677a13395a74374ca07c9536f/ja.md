```
OpenStreetMapSpace(path::AbstractString; kwargs...)
```

指定された `path` を介して提供された Open Street Map (OSM) ファイルに存在する空間を作成します。この空間は、パフォーマンスよりも精度を選択する *連続的* な実体としての基盤となる地図を表します。地図は、エッジで接続されたノードからなるグラフとして表現されます。ノードは必ずしも交差点ではなく、2つの交差点を結ぶ道路上に複数のノードが存在する場合があります。エージェントは、以下に示すルーティングを使用して地図の利用可能な道路に沿って移動します。

Open Street Map 空間に関連する機能は、サブモジュール `OSM` にあります。その使用例は [Zombie Outbreak in a City](@ref) で見つけることができます。

## `OSMAgent`

`OSMSpace` に存在するエージェントの基本プロパティは次のとおりです。

```julia
mutable struct Agent <: AbstractAgent
    id::Int
    pos::Tuple{Int,Int,Float64}
end
```

現在の `pos` 位置タプルは (最初の交差点インデックス, 2 番目の交差点インデックス, 移動距離) として表されます。インデックスは、地図を内部的に表現するグラフのノードのインデックスです。関数 [`OSM.nearest_node`](@ref) や [`OSM.nearest_road`](@ref) を使用すると、(lon, lat) 実世界座標からこれらのノードインデックスを見つけるのに役立ちます。移動距離は `weight_type` の単位で表されます。これにより、地図は *連続的* な種類の空間となり、エージェントは実際に既存の道路上の任意のポイントに存在することができます。

便利のために [`OSMAgent`](@ref OSM.OSMAgent) を使用してください。

## 地図ファイルの取得

地図ファイルは、[LightOSM.jl](https://github.com/DeloitteDigitalAPAC/LightOSM.jl) によって提供される関数を使用してダウンロードできます。Agents.jl はまた、地図をダウンロードするために使用される主要な関数である [`OSM.download_osm_network`](@ref) を再エクスポートし、[`OSM.test_map`](@ref) にテストマップを提供します。ロンドンの地図を `"london.json"` にダウンロードするための使用例：

```julia
OSM.download_osm_network(
    :place_name;
    place_name = "London",
    save_to_file_location = "london.json"
)
```

2つのノード間のエッジの長さは、[`LightOSM.OSMGraph`](https://deloittedigitalapac.github.io/LightOSM.jl/docs/types/#LightOSM.OSMGraph) のドキュメントに記載されている地図の `weight_type` の単位で指定されます。可能な `weight_type` は次のとおりです：

  * `:distance`: エッジの距離（キロメートル）
  * `:time`: その道路で許可されている最大速度でエッジに沿って移動するのにかかる時間（時間）
  * `:lane_efficiency`: 車線数でスケーリングされた時間

使用されるデフォルトの `weight_type` は `:distance` です。

すべての `kwargs` は [`LightOSM.graph_from_file`](https://deloittedigitalapac.github.io/LightOSM.jl/docs/create_graph/#LightOSM.graph_from_file) に伝播されます。

## OSMによるルーティング

[`plan_route!`](@ref) または [`plan_random_route!`](@ref) を使用できます。実際に計画されたルートに沿って移動するには、[`move_along_route!`](@ref) を使用します。 ```
