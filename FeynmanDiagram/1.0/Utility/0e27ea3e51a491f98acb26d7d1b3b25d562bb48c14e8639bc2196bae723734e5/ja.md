```
function taylorAD(graphs::Vector{G}, deriv_orders::Vector{Int}, leaf_dep_funcs::Vector{Function};
    dict_graphs::Dict{Vector{Int},Vector{Graph}}=Dict{Vector{Int},Vector{Graph}}()
) where {G<:Graph}

ベクトルのグラフに対してテイラー方式の自動微分（AD）を実行します。微分プロセスは、指定された最大微分次数と葉依存関数に基づいて調整されます。微分されたグラフは、その微分次数に基づいて辞書に分類されます。
```

# パラメータ

  * `graphs`: 微分されるグラフのベクトル。
  * `deriv_orders`: グラフに適用する最大微分次数を指定する整数のベクトル。
  * `leaf_dep_funcs`: グラフの葉の特性に対する微分変数の依存性を決定する関数のベクトル。
  * `dict_graphs`: オプション。特定の微分次数を表す整数のベクトルによってキー付けされた出力グラフを格納するための辞書。デフォルトは空の辞書です。

# 戻り値

  * `Dict{Vector{Int},Vector{Graph}}`: テイラー方式のADを通じて処理されたグラフを含む辞書で、微分次数によって分類されています。

# 使用例

```julia
# グラフのベクトルを定義
graphs = [g1, g2]
# 最大微分次数を指定
deriv_orders = [2, 3, 3]

# 葉の特性に対する微分依存関数のベクトルを定義。 
# 最初と二番目の関数は、`BareGreenId`および`BareInteractionId`特性をそれぞれグリーン関数および相互作用カウンタ項として特定します。
# 三番目の関数は、葉の最初の外部運動量への依存性を指定します。
leaf_dep_funcs = [pr -> pr isa FrontEnds.BareGreenId, pr -> pr isa FrontEnds.BareInteractionId, pr -> pr.extK[1] != 0]

# テイラー方式のADを実行し、結果を分類します。`result_dict`は、微分次数`[0:2, 0:3, 0:3]`によって整理されたAD結果を保持します。
result_dict = taylorAD(graphs, deriv_orders, leaf_dep_funcs)
```
