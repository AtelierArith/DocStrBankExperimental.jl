与えられた引用キーグループのリストに基づいて、指定されたCSLおよびbibtexで提供された参考文献に基づいてインライン引用を作成します。

## 引数

  * `citation_groups::Vector{String}` - 引用キーグループを含む文字列のベクター
  * `bibtex_path::String` - 参考文献へのパス（`.bib`形式がサポートされています）
  * `csl_path::String` - CSL標準へのパス（すなわち、`.csl`形式）

## 戻り値

  * 元の引用グループをキーとし、それに対応するインライン引用を値とする辞書
