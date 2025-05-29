```
generate_property_graph!(::Client, round_type::MBQC, resource::MBQCResourceState, state_type::Union{StateVector,DensityMatrix})
```

この関数は、ラウンドタイプに基づいてMBQCモデルのクライアントのプロパティグラフを生成します。最初にリソースからメタグラフを作成し、ラウンドタイプを追加します。次に、出力キュービットを追加し、頂点タイプとIOキュービットタイプを設定し、キュービットを初期化し、フローヴェルテックスと補正ヴェルテックスを追加し、測定結果を初期化し、メタグラフの量子状態を初期化し、グラフをエンタングルします。この関数は、各ラウンドの開始時に実行されます。

# 引数

  * `::Client`: クライアントオブジェクト。
  * `round_type::MBQC`: ラウンドタイプ。
  * `resource::MBQCResourceState`: グラフとその色付けを含むリソース。
  * `state_type::Union{StateVector,DensityMatrix}`: 作成する量子状態のタイプ。

# 戻り値

  * 更新されたMetaGraph。

# 例

```julia
client = Client()
resource = MBQCResourceState(graph)
round_type = MBQC()
state_type = StateVector()
generate_property_graph!(client, round_type, resource, state_type)
```
