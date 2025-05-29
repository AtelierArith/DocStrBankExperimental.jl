```
add_blanks(query_path::String, db_path::String, character_labels::Dict{String,String},
character_labels_no_gaps::Dict{String,String} ; return_blast::Bool=false)
```

入力シーケンスにデータベースを基にブランクを追加します。

# 引数

  * `query_path::String`: クエリファイルへのパス。
  * `db_path::String`: blastデータベースへのパス。
  * `character_labels::Dict{String,String}`: 文字ラベルと対応するシーケンスのマッピング。
  * `character_labels_no_gaps::Dict{String,String}`: シーケンスからギャップを除いた文字ラベル。
  * `return_blast::Bool=false`: blast結果を返すかどうか。
  * `protein::Bool=false`: タンパク質シーケンスかどうか。
