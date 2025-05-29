```julia
reduce(α::DecisionDiagram{T}, cache::Dict{Tuple{Int,Int,Int},DecisionDiagram{T}}, vcache::Dict{T,DecisionDiagram{T}}) 

決定図αの標準形をノードおよび値キャッシュを使用して返します。図は標準形であるためには、以下の条件を満たす必要があります：     - 2つの端末が同じ値に割り当てられていないこと     - 2つのノードが同じ変数でラベル付けされ、同じ2つの縮小された子ノード（低および高）を持ち、同一のIDを持たないこと

# 引数

  * `α`: 縮小する決定図。
  * `cache`: 内部ノードのキャッシュ（変数、低および高の子ノードのIDによって識別される）。
  * `vcache::Dict{T,DecisionDiagram{T}}`: 関連する値によって識別される端末ノードのキャッシュ。
```
