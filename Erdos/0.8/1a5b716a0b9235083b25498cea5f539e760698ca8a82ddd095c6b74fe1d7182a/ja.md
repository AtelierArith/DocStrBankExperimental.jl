```
maximum_flow{T<:Number}(
                    g::ADiGraph,
                    source::Int,
                    target::Int,
                    capacity_matrix::AbstractMatrix{T} =
                        DefaultCapacity(g);
                    algorithm::AbstractFlowAlgorithm  =
                        PushRelabelAlgorithm(),
                    restriction::T = zero(T)
                )
```

汎用の最大*フロー関数です。この関数はデフォルトでプッシュ-リラベル（プレフローとも呼ばれる）アルゴリズムを使用します。代わりに、使用するアルゴリズムはキーワード引数を通じて指定することもできます。容量行列が提供されていない場合、各リンクのデフォルト容量は1と見なされます。制限が0より大きい場合、それはcapacity*matrixに適用されます。

すべてのアルゴリズムは、次のタプルを返します。

1. 最大フロー
2. フローマトリックス
3. 最小カットに関連付けられたラベリング

利用可能なアルゴリズムは`DinicAlgorithm`、`EdmondsKarpAlgorithm`、`BoykovKolmogorovAlgorithm`、および`PushRelabelAlgorithm`です。

プッシュリラベルアルゴリズムの時間計算量はO(V²√E)です。

### 使用例:

```julia

# フローグラフと容量行列を作成
g = DiGraph(8)
flow_edges = [
    (1,2,10),(1,3,5),(1,4,15),(2,3,4),(2,5,9),
    (2,6,15),(3,4,4),(3,6,8),(4,7,16),(5,6,15),
    (5,8,10),(6,7,15),(6,8,10),(7,3,6),(7,8,10)
]
capacity_matrix = zeros(Int, 8, 8)
for e in flow_edges
    u, v, f = e
    add_edge!(g, u, v)
    capacity_matrix[u,v] = f
end

# capacity_matrixなしでデフォルトのmaximum_flowを実行（各エッジの容量は1と仮定）。
f, F, labels = maximum_flow(g, 1, 8)

# エドモンズ-カープアルゴリズムを実行
f, F, labels = maximum_flow(g,1,8,capacity_matrix,algorithm=EdmondsKarpAlgorithm())
```
