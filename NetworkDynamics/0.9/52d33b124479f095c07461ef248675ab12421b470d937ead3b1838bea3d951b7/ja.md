```
Network([g,] vertexf, edgef; kwarg...)
```

グラフ `g` とエッジおよびコンポーネントモデル `vertexf` と `edgef` から `Network` オブジェクトを構築します。

引数:

  * `g::AbstractGraph`: ネットワークが定義されるグラフ。オプションで、すべてのコンポーネントモデルに `graphelement` が定義されている場合は省略可能です。 [`VertexModel`](@ref) および [`EdgeModel`](@ref) コンストラクタの `vidx` および `src`/`dst` キーワードを参照してください。
  * `vertexm`: 単一の [`VertexModel`](@ref) または [`VertexModel`](@ref) オブジェクトのベクター。頂点モデルの順序は `vertices(g)` イテレータの順序と一致しなければなりません。
  * `edgem`: 単一の [`EdgeModel`](@ref) または [`EdgeModel`](@ref) オブジェクトのベクター。エッジモデルの順序は `edges(g)` イテレータの順序と一致しなければなりません。

オプションのキーワード引数:

  * `execution=SequentialExecution{true}()`: ネットワークの実行モデル。例: [`SequentialExecution`](@ref)、[`KAExecution`](@ref)、[`PolyesterExecution`](@ref) または [`ThreadedExecution`](@ref)。
  * `aggregator=execution isa SequentialExecution ? SequentialAggregator(+) : PolyesterAggregator(+)`: エッジモデルに適用される集約関数。例: [`SequentialAggregator`](@ref)、[`PolyesterAggregator`](@ref)、[`ThreadedAggregator`](@ref)、[`SparseAggregator`](@ref)。
  * `check_graphelement=true`: `graphelement` メタデータがグラフと一貫しているかどうかを確認します。
  * `dealias=false`: コンポーネントが互いにエイリアスしているかどうかを確認し、必要に応じてコピーを作成します。これは、同じコンポーネントモデルがネットワーク内の複数の場所で参照されているが、特定のインスタンスに初期化情報などのメタデータを動的に割り当てたい場合に必要です。
  * `verbose=false`: 構築中に追加情報を表示します。

```
