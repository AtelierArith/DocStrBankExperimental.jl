```
df = join(stats, cols; kwargs...)
```

`stats`で与えられたDataFrameの辞書を結合します。すべてのDataFrameに`:id`列が必要です。結果のDataFrameには、各ソルバーのための`id`列とすべての`cols`列が含まれます。

入力:

  * `stats::Dict{Symbol,DataFrame}`: ソルバーごとのDataFrameの辞書。各キーは異なるソルバーです;
  * `cols::Array{Symbol}`: DataFrameのどの列を使用するか。

キーワード引数:

  * `invariant_cols::Array{Symbol,1}`: 追加される不変列、すなわち、ソルバーに依存しない列（問題の名前、変数の数など）;
  * `hdr_override::Dict{Symbol,String}`: ヘッダー名の上書き。

出力:

  * `df::DataFrame`: 結果のDataFrame。
