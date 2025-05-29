```
show(io::IO, mime::MIME, df::AbstractDataFrame)
```

MIMEタイプ`mime`でI/Oストリームにデータフレームをレンダリングします。

# 引数

  * `io::IO`: `df`が印刷されるI/Oストリーム。
  * `mime::MIME`: サポートされているMIMEタイプは次のとおりです: `"text/plain"`, `"text/html"`, `"text/latex"`, `"text/csv"`, `"text/tab-separated-values"`（最後の2つのMIMEタイプは`#undef`値の表示をサポートしていません）
  * `df::AbstractDataFrame`: 印刷するデータフレーム。

さらに選択されたMIMEタイプは、次のキーワード引数を受け入れます：

  * MIMEタイプ`"text/plain"`は、すべてのリストされたキーワード引数を受け入れ、その動作は`show(::IO, ::AbstractDataFrame)`と同じです。
  * MIMEタイプ`"text/html"`は、次のキーワード引数を受け入れます：

      * `eltypes::Bool = true`: 列名の下に列の型を印刷するかどうか。
      * `summary::Bool = true`: データフレームの簡潔な文字列要約を印刷するかどうか。
      * `max_column_width::AbstractString = ""`: 最大列幅。これは有効なCSS長を含む文字列でなければなりません。たとえば、`"100px"`を渡すと、すべての列の幅が100ピクセルに制限されます。空の場合、列は制限なしでレンダリングされます。
      * `kwargs...`: PrettyTables.jlの`pretty_table`関数によってサポートされる任意のキーワード引数をここで渡して出力をカスタマイズできます。

# 例

```jldoctest
julia> show(stdout, MIME("text/latex"), DataFrame(A=1:3, B=["x", "y", "z"]))
\begin{tabular}{r|cc}
	& A & B\\
	\hline
	& Int64 & String\\
	\hline
	1 & 1 & x \\
	2 & 2 & y \\
	3 & 3 & z \\
\end{tabular}
14

julia> show(stdout, MIME("text/csv"), DataFrame(A=1:3, B=["x", "y", "z"]))
"A","B"
1,"x"
2,"y"
3,"z"
```
