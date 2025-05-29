```
mutable struct Graph{F<:Number,W}
```

計算グラフの表現、例えば、式木で、型が安定したノードデータを持ちます。

# メンバー:

  * `id::Int`  図を識別するための一意のハッシュID
  * `name::Symbol`  図の名前
  * `orders::Vector{Int}`  グラフに関連するオーダー、例えば、導関数のオーダー
  * `subgraphs::Vector{Graph{F,W}}`  サブダイアグラムのベクター
  * `subgraph_factors::Vector{F}`  各サブグラフに関連するスカラー乗法因子。サブグラフ因子は代数的に操作可能であることに注意してください。このグラフに意味のある固定の乗法因子を関連付けるには、代わりに `factor` 引数を使用してください。
  * `operator::DataType`  ノード操作。加算と乗算は、それぞれ Sum と Prod 演算子を介してネイティブにサポートされています。`AbstractOperator` の具体的なサブタイプである必要があります。
  * `weight::W`  このノードの重み
  * `properties::Any` グリーン関数の追加情報。

# 例:

```julia-repl
julia> g1 = Graph([])
1=0.0

julia> g2 = Graph([]; factor=2)
2⋅2.0=0.0

julia> g = Graph([g1, g2]; operator=ComputationalGraphs.Sum())
3=0.0=⨁ (1,2)
```
