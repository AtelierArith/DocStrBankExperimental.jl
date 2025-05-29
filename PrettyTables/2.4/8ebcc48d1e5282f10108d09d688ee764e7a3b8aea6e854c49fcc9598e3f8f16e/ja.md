```
struct LatexTableFormat
```

この構造体はLaTeXテーブルのフォーマットを定義します。

# フィールド

  * `top_line::String`: テーブルの上部の行。
  * `header_line::String`: ヘッダーとテーブル本体を分ける行。
  * `mid_line::String`: テーブルの中央に印刷される行。
  * `bottom_line::String`: テーブルの下部の行。
  * `left_vline::String`: テーブルの左の垂直線。
  * `mid_vline::String`: テーブルの中央の垂直線。
  * `right_vline::String`: テーブルの右の垂直線。
  * `header_envs::Vector{String}`: 各ヘッダーセルで使用されるLaTeX環境。
  * `subheader_envs::Vector{String}`: 各サブヘッダーセルで使用されるLaTeX環境。
  * `hlines::Vector{Symbol}`: デフォルトで描画されるべき水平線。
  * `vlines::Union{Symbol, Vector{Symbol}}`: デフォルトで描画されるべき垂直線。
  * `table_type::Symbol`: このフォーマットに使用されるべきテーブルのタイプを選択します。
  * `wrap_table::Bool`: テーブルが`wrap_table_environment`で定義された環境内にラップされるべきかどうかを選択します。
  * `wrap_table_environment::String`: `wrap_table`がtrueの場合、テーブルがラップされる環境。
