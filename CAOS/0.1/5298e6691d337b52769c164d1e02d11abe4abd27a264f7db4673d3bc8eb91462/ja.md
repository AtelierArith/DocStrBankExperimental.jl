```
classify_new_sequence(tree::Node, character_labels::Dict{String,String}, taxa_labels::Dict{String,String},
sequence_file_path::String, output_directory::String ; all_CA_weights::Dict{Int64,
Dict{String,Int64}}=Dict(1=>Dict("sPu"=>1,"sPr"=>1,"cPu"=>1,"cPr"=>1)), occurrence_weighting::Bool=false,
tiebreaker::Vector{Dict{String,Int64}}=[Dict{String,Int64}()], combo_classification::Bool=false)
```

ツリー（Node）とシーケンスを受け取り、新しいシーケンスをCAOSツリーを使用して分類します。

# 引数

  * `tree::Node`: Nodeとして表現されたツリー。
  * `character_labels::Dict{String,String}`: キャラクタラベルを対応するシーケンスにマッピングしたもの。
  * `taxa_labels::Dict{String,String}`: タクサラベルをキャラクタラベルにマッピングしたもの。
  * `sequence_file_path::String`: 分類するシーケンスへのファイルパス。
  * `output_directory::String`: 出力ディレクトリへのパス。
  * `all_CA_weights::Dict{Int64,Dict{String,Int64}}=Dict(1=>Dict("sPu"=>1,"sPr"=>1,"cPu"=>1,"cPr"=>1))`: 使用するCAウェイト。
  * `occurrence_weighting::Bool=false`: 分類において出現重み付けを使用するかどうか。
  * `tiebreaker::Vector{Dict{String,Int64}}=[Dict{String,Int64}()]`: 分類において使用するタイブレイカー。
  * `combo_classification::Bool=false`: 分類においてBlastとCAOSのコンボを使用するかどうか。
