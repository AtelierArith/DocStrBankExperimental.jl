```
mutable struct FeynmanGraph{F<:Number,W}

計算グラフの表現 (コレクションの) ファインマン図。すべてのファインマン図は、同じ外部および内部の頂点のセットを共有する必要があります。
```

# メンバー:

  * `id::Int`  図を識別するための一意のハッシュID
  * `name::Symbol`  図の名前
  * `orders::Vector{Int}`  ファインマングラフに関連する次数、例：ループ/導関数次数
  * `properties::FeynmanProperties`  図的特性、例：演算子頂点とトポロジー
  * `subgraphs::Vector{FeynmanGraph{F,W}}`  サブ図のベクター
  * `subgraph_factors::Vector{F}`  各サブ図に関連するスカラー乗法因子
  * `operator::DataType`  ノード操作 (和、積など)
  * `weight::W`  図の重み

# 例:

```julia-repl
julia> g1 = FeynmanGraph([]; vertices=[𝑓⁺(1),𝑓⁻(2)], external_indices=[1,2], external_legs=[true,true])
1:f⁺(1)|f⁻(2)=0.0

julia> g2 = FeynmanGraph([]; vertices=[𝑓⁺(3),𝑓⁻(4)], external_indices=[1,2], external_legs=[true,true])
2:f⁺(3)|f⁻(4)=0.0

julia> g = FeynmanGraph([g1,g2]; vertices=[𝑓⁺(1),𝑓⁻(2),𝑓⁺(3),𝑓⁻(4)], operator=ComputationalGraphs.Prod(), external_indices=[1,2,3,4], external_legs=[true,true,true,true])
3:f⁺(1)|f⁻(2)|f⁺(3)|f⁻(4)=0.0=Ⓧ (1,2)
```
