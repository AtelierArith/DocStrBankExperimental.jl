```
initialise_quantum_state_meta_graph!(mbqc::MBQC, client::Client, state_type::Union{StateVector,DensityMatrix}, mg)
```

この関数は、MBQCモデルのクライアントのためにメタグラフの量子状態を初期化します。最初に、量子環境と指定されたタイプの量子状態を作成します。次に、メタグラフの各頂点について、頂点のタイプと頂点のIOタイプを取得し、これらを使用して量子状態のキュービットを初期化します。最後に、量子状態をメタグラフのプロパティとして設定します。

# 引数

  * `::MBQC`: MBQCオブジェクト。
  * `::Client`: クライアントオブジェクト。
  * `state_type::Union{StateVector,DensityMatrix}`: 作成する量子状態のタイプ。
  * `mg`: プロパティが追加されるメタグラフ。

# 戻り値

  * 更新されたメタグラフ。

# 例

```julia
mbqc = MBQC()
client = Client()
mg = MetaGraphs.MetaGraph(graph)
state_type = StateVector()
initialise_quantum_state_meta_graph!(mbqc, client, state_type, mg)
```
