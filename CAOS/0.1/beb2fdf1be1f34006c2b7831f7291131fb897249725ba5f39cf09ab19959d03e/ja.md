```
classify_sequence(sequence::String, tree::Node, CA_weights::Dict{String,Int64},
all_CA_weights::Dict{Int64,Dict{String,Int64}}, occurrence_weighting::Bool,
depth::Int64, tiebreaker::Vector{Dict{String,Int64}} ; blast_results=["Fake Label"], combo_classification::Bool=false, protein::Bool=false)
```

入力シーケンスを系統樹に基づいて分類します。

# 引数

  * `sequence::String`: 一致をカウントするシーケンス。
  * `tree::Node`: ノードとして表現された木。
  * `CA_weights::Dict{String,Int64}`: CAカウントに使用する重み。
  * `all_CA_weights::Dict{Int64,Dict{String,Int64}}`: CAカウントに使用するすべての重みのセット。
  * `occurrence_weighting::Bool`: カウント中に出現重み付けを使用するかどうか。
  * `depth::Int64`: 木の現在の深さ。
  * `tiebreaker::Vector{Dict{String,Int64}}`: 使用するタイブレイキング手続き。
  * `blast_results=["Fake Label"]`: ブラスト結果のリスト。
  * `combo_classification::Bool=false`: 分類にBlastとCAOSの両方を使用するかどうか。
