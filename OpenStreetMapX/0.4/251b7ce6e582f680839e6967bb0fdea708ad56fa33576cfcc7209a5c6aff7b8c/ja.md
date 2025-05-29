```
get_map_data(filepath::String,filename::Union{String,Nothing}=nothing;
             road_levels::Set{Int} = Set(1:length(OpenStreetMapX.ROAD_CLASSES)),
			 use_cache::Bool = true, only_intersections::Bool=true)::MapData
```

高レベルの関数 - .osmファイルを解析し、マップデータに基づいて道路ネットワークを作成します。このコードは現在、*.osmおよび*.pbf (@blegat - ありがとうございます!) ファイルの両方を解析できます。データ型はファイル拡張子によって決まります。

**引数**

  * `filepath` : .osm/.pbfファイルのパス（ディレクトリまたはファイルへのパス）
  * `filename` : ファイルの名前（最初の引数がディレクトリの場合）
  * `road_levels` : 道路カテゴリのセット（詳細についてはOpenStreetMapX.ROAD_CLASSESを参照）
  * `use_cache` : `datapath`フォルダにシリアライズされたマップ画像を持つ*.cacheファイルが作成されます
  * `only_intersections` : 道路システムデータのみを含める
  * `trim_to_connected_graph`: マップが強連結グラフになるように孤立ノードをトリムします
