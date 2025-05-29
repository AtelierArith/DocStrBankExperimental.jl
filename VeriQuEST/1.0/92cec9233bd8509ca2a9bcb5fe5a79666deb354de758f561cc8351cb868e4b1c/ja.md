```
initialise_quantum_state_meta_graph!(::Client, state_type::Union{StateVector,DensityMatrix}, mg)
```

この関数は、MBQCモデルのクライアントのメタグラフの量子状態を初期化します。最初に、量子環境と指定されたタイプの量子状態を作成します。次に、メタグラフの各頂点について、頂点のタイプ、頂点のIOタイプ、および初期キュービット値を取得し、これらを使用して量子状態のキュービットを初期化します。最後に、量子状態をメタグラフのプロパティとして設定します。

# 引数

  * `::Client`: クライアントオブジェクト。
  * `state_type::Union{StateVector,DensityMatrix}`: 作成する量子状態のタイプ。
  * `mg`: プロパティが追加されるメタグラフ。

# 戻り値

  * 更新されたメタグラフ。

# 例

```julia
client = Client()
mg = MetaGraphs.MetaGraph(graph)
state_type = StateVector()
initialise_quantum_state_meta_graph!(client, state_type, mg)
```
