```
get_sPu_and_sPr(nodes::Array{Dict{String,Any}}, node_num::Int64,
taxa_labels::Dict{String,String}, character_labels::Dict{String,String})
```

特定のノードでの全体のキャラクターシーケンスに対するすべてのsPuとsPrを取得します。

# 引数

  * `nodes::Array{Dict{String,Any}}`: ノードのリスト。
  * `node_num::Int64`: 現在のノードインデックス。
  * `taxa_labels::Dict{String,String}`: 種ラベルをキャラクターラベルにマッピングします。
  * `character_labels::Dict{String,String}`: キャラクターラベルを対応するシーケンスにマッピングします。
