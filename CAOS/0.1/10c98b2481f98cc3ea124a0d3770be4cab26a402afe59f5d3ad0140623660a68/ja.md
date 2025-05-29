```
add_nodes!(tree::Node,sPu::Array{Dict{String,Any}},sPr::Array{Dict{String,Any}},
cPu::Array{Dict{String,Any}},cPr::Array{Dict{String,Any}},taxa_labels::Dict{String,String},
character_labels::Dict{String,String},nodes::Array{Dict{String,Any}},node_num::Int64;complex::Bool=true)
```

ツリー（Node）を取り込み、ツリー全体からすべてのCAを内部表現に追加します。

# 引数

  * `tree::Node`: Nodeとして表現されたツリー。
  * `sPu::Array{Dict{String,Any}}`: 単純な純粋ルールの配列。
  * `sPr::Array{Dict{String,Any}}`: 単純なプライベートルールの配列。
  * `cPu::Array{Dict{String,Any}}`: 複雑な純粋ルールの配列。
  * `cPr::Array{Dict{String,Any}}`: 複雑なプライベートルールの配列。
  * `taxa_labels::Dict{String,String}`: 種ラベルをキャラクタラベルにマッピングする辞書。
  * `character_labels::Dict{String,String}`: キャラクタラベルを対応するシーケンスにマッピングする辞書。
  * `nodes::Array{Dict{String,Any}}`: ノードの配列。
  * `node_num::Int64`: 現在のノード番号。
  * `complex::Bool=true`: 複雑なルールを計算するかどうかを示します。
  * `protein::Bool=false`: データセットがタンパク質（またはヌクレオチド）であるかどうかを示します。
