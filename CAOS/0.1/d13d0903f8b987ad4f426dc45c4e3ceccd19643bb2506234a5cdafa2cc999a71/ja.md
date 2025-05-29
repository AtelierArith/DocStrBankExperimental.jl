```
get_cPu_and_cPr(nodes::Array{Dict{String,Any}}, node_num::Int64, taxa_labels::Dict{String,String},
character_labels::Dict{String,String}, sPu::Array{Dict{String,Any}}, sPr::Array{Dict{String,Any}})
```

特定のノードでの全キャラクターシーケンスに対するすべてのcPuとcPrを取得します（ヌクレオチドオプションはサポートされていません）。

# 引数

  * `nodes::Array{Dict{String,Any}}`: ノードのリスト。
  * `node_num::Int64`: 現在のノードインデックス。
  * `taxa_labels::Dict{String,String}`: 種ラベルをキャラクタラベルにマッピングする辞書。
  * `character_labels::Dict{String,String}`: キャラクタラベルを対応するシーケンスにマッピングする辞書。
  * `sPu::Array{Dict{String,Any}}`: 単純な純粋ルールのリスト。
  * `sPr::Array{Dict{String,Any}}`: 単純なプライベートルールのリスト。
