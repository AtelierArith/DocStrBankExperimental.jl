```
function leafstates(leaf_maps::Vector{Dict{Int,G}}, labelProd::LabelProduct) where {G<:Union{Graph,FeynmanGraph}}

葉の値のインデックスから葉ノードへの葉マッピングから葉情報を抽出します。すべてのグラフパーティションとそれに関連するLabelProductデータ（`labelProd`）に対して行います。
情報には、初期値、タイプ、オーダー、入出力時間、およびループモーメンタが含まれます。
```

# 引数:

  * `leaf_maps`: 葉の値のインデックスをこの葉のFeynmanGraph/Graphにマッピングする辞書のベクター。各辞書は、（order、Gorder、Vorder）などのグラフパーティションに対応します。
  * `labelProd`: グラフの葉にラベルを付けるために使用されるLabelProduct。

# 戻り値

  * グラフの葉に関する情報を含むベクターのタプル。初期値、タイプ、オーダー、入力および出力時間インデックス、ループモーメンタインデックスが含まれます。
