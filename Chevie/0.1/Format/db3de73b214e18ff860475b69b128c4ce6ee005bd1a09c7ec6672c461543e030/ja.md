`showtable(io::IO=stdout, table::AbstractMatrix; keywords)`

REPL、`IJulia`、または`Pluto`でテーブルをフォーマットするための一般的なルーチンです。`table`の要素およびキーワード内のラベルは任意の型であり、`io`のコンテキストでフォーマットされますが、文字列`s`は`fromTeX(io,s)`によってフォーマットされます。次のオプションは、`io`のプロパティまたはキーワードとして渡すことができます。

  * `row_labels`: 行のラベル。`Vector{Any}`（文字列も可）、デフォルトは`axes(table,1)`
  * `rows_label`: 行ラベルの最初の列のラベル（デフォルトはなし）
  * `col_labels`: 他の列のラベル（デフォルトはなし）
  * `align`: "lcr"のいずれかの文字：列の整列（デフォルトは'r'）；その後、すべての列は指定されたように整列されますが、`rows_labels`は常に左に整列されます。また、`align`が文字列の場合は、長さ`1+size(table,2)`である必要があり、最初の文字は`row_labels`の整列です。
  * `row_seps`: セパレーターを置く行番号。`i`の数はテーブルの`i`-th行の前を意味します。したがって、`0`はテーブルの最上部、`-1`は`col_labels`の前です。デフォルトは`[-1,0,size(table,1)]`です。
  * `col_seps`: セパレーターを置く列番号。`i`の数はテーブルの`i`-th列の前を意味します。したがって、`0`はテーブルの左側、`-1`は`row_labels`の前です。デフォルトは`[-1,0,size(table,2)]`です。代わりに、`col_seps`はLaTeXスタイルの`align`文字列`|r|llll|`を使用して指定できます。2つの方法のうちの1つだけで指定する必要があります。
  * `rows`: これらの行のみを表示します。デフォルトはすべての行：`axes(table,1)`
  * `cols`: これらの列のみを表示します。デフォルトはすべての列：`axes(table,1)`
  * `TeX`: デフォルトは`false`。`true`の場合、LaTeX出力を提供します（JupyterやPlutoでより良い出力を提供するのに便利です）
  * `column_repartition`: `Vector{<:Integer}`。指定されたサイズの垂直の部分で表示します（`TeX`に便利：そうでなければ、`displaysize(io,2)`を考慮して自動的に列の再分配が計算されます）。
  * `dotzero`: `true`の場合、テーブル内の'0'を'.'に置き換えます（デフォルトはfalse）。

```julia-rep1
julia> m=reshape(1:10:120,3,4)
3×4 reshape(::StepRange{Int64, Int64}, 3, 4) with eltype Int64:
  1  31  61   91
 11  41  71  101
 21  51  81  111

julia> showtable(m)
┌─┬────────────┐
│1│ 1 31 61  91│
│2│11 41 71 101│
│3│21 51 81 111│
└─┴────────────┘

julia> labels=["x","y","z","t"];

julia> showtable(m;cols=2:4,col_labels=labels,row_seps=[0,2,3])
    y  z   t 
┌─┬─────────┐
│1│31 61  91│
│2│41 71 101│
├─┼─────────┤
│3│51 81 111│
└─┴─────────┘

julia> showtable(m;col_labels=labels,rows_label="N",align="|r|ll|ll|")
┌─┬─────┬──────┐
│N│ x  y│ z   t│
├─┼─────┼──────┤
│1│1  31│61 91 │
│2│11 41│71 101│
│3│21 51│81 111│
└─┴─────┴──────┘
```
