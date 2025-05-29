与えられた引用キーグループのリストに基づいて、指定されたCSLとbibtex文献リストに基づいて参照リストを作成します。

## 引数

  * `citation_groups::Vector{String}` - 引用キーグループを含む文字列のベクター
  * `bibtex_path::String` - 文献リストへのパス（`.bib`形式がサポートされています）
  * `csl_path::String` - CSL標準へのパス（すなわち、`.csl`形式）

## 戻り値

  * 整列された参照リストを含む文字列
