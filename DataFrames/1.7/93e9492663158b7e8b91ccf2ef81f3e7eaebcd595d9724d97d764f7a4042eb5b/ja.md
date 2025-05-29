```
show([io::IO, ]df::AbstractDataFrame;
     allrows::Bool = !get(io, :limit, false),
     allcols::Bool = !get(io, :limit, false),
     allgroups::Bool = !get(io, :limit, false),
     rowlabel::Symbol = :Row,
     summary::Bool = true,
     eltypes::Bool = true,
     truncate::Int = 32,
     kwargs...)
```

データフレームをI/Oストリームにレンダリングします。選択された特定の視覚表現は、表示の幅に依存します。

`io`が省略されると、結果は`stdout`に印刷され、`allrows`、`allcols`、および`allgroups`はデフォルトで`false`になります。

# 引数

  * `io::IO`: `df`が印刷されるI/Oストリーム。
  * `df::AbstractDataFrame`: 印刷するデータフレーム。
  * `allrows::Bool`: デバイスの高さに収まる部分集合ではなく、すべての行を印刷するかどうか。デフォルトでは、`io`に`IOContext`プロパティ`limit`が設定されていない場合のみ、これが適用されます。
  * `allcols::Bool`: デバイスの幅に収まる部分集合ではなく、すべての列を印刷するかどうか。デフォルトでは、`io`に`IOContext`プロパティ`limit`が設定されていない場合のみ、これが適用されます。
  * `allgroups::Bool`: `df`が`GroupedDataFrame`の場合、最初と最後ではなく、すべてのグループを印刷するかどうか。デフォルトでは、`io`に`IOContext`プロパティ`limit`が設定されていない場合のみ、これが適用されます。
  * `rowlabel::Symbol = :Row`: 行番号を含む列に使用するラベル。
  * `summary::Bool = true`: データフレームの簡潔な文字列要約を印刷するかどうか。
  * `eltypes::Bool = true`: 列名の下に列の型を印刷するかどうか。
  * `truncate::Int = 32`: 出力が切り捨てられる前に使用できる最大表示幅（`textwidth`の意味で、`…`を除く）。`truncate`が0以下の場合、切り捨ては適用されません。
  * `kwargs...`: PrettyTables.jlの`pretty_table`関数がサポートする任意のキーワード引数をここに渡して出力をカスタマイズできます。

# 例

```jldoctest
julia> using DataFrames

julia> df = DataFrame(A=1:3, B=["x", "y", "z"]);

julia> show(df, show_row_number=false)
3×2 DataFrame
 A      B
 Int64  String
───────────────
     1  x
     2  y
     3  z
```
