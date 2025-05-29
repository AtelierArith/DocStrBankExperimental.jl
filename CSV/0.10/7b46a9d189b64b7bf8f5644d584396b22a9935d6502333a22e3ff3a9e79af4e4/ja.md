```
CSV.write(file, table; kwargs...) => file
table |> CSV.write(file; kwargs...) => file
```

`IO` 引数または書き込むファイル名を表す `String`/FilePaths.jl 型を指定して、[Tables.jl インターフェース入力](https://github.com/JuliaData/Tables.jl) を csv ファイルに書き込みます。あるいは、`CSV.RowWriter` は行イテレータを作成し、入力テーブルの各行に対して csv 形式の文字列を生成します。

サポートされているキーワード引数は次のとおりです：

  * `bufsize::Int=2^22`: 各 csv 形式の行を書き込むときに使用するバッファの長さ; デフォルトは 4MB; 行が `bufsize` より大きい場合はエラーが発生します
  * `delim::Union{Char, String}=','`: ファイルの区切り文字として出力する文字または文字列
  * `quotechar::Char='"'`: 区切り文字や改行を含む可能性のあるテキストフィールドを引用するために使用する ascii 文字
  * `openquotechar::Char`: `quotechar` の代わりに、異なる開始および終了引用文字をサポートするために `openquotechar` と `closequotechar` を使用します
  * `escapechar::Char='"'`: テキストフィールド内の引用文字をエスケープするために使用される ascii 文字
  * `missingstring::String=""`: `missing` 値のために出力する文字列
  * `dateformat=Dates.default_format(T)`: `Date` および `DateTime` 列を出力するために使用する日付形式文字列
  * `append=false`: 既存のファイル/IO への書き込みを追加するかどうか; `true` の場合、デフォルトでは列名は書き込まれません
  * `compress=false`: 標準の gzip 圧縮を使用して書き込まれた出力を圧縮します（CodecZlib.jl パッケージによって提供されます）; 圧縮ストリームは常に最初の「ファイル」引数として提供でき、他の形式の圧縮をサポートします; `compress=true` を渡すのは、手動で GzipCompressorStream を設定する必要がないようにするための便利さのためです
  * `writeheader=!append`: 列名の区切られた初期行を書き込むかどうか; 追加の場合はデフォルトでは書き込まれません
  * `header`: 入力テーブルの列名の代わりに使用する列名のリスト（シンボルまたは文字列）を渡します
  * `newline='\n'`: 行（csv ファイル内の行）を区切るために使用する文字または文字列
  * `quotestrings=false`: すべての文字列を引用するかどうか
  * `decimal='.'`: 浮動小数点数を書き込むときに小数点として使用する文字
  * `transform=(col,val)->val`: 各セルに適用される関数; 例えば、`(col, val) -> something(val, missing)` を使用してすべての `nothing` 値を `missing` に変換できます
  * `bom=false`: UTF-8 BOM ヘッダー (0xEF 0xBB 0xBF) を書き込むかどうか
  * `partition::Bool=false`: `true` を渡すことで、`table` 引数は `Tables.partitions` を実装していることが期待され、`file` 引数は `IO` のインデックス可能なコレクション、ファイル `String`、または名前にインデックスが追加される単一のファイル `String` であることができます

## 例

```julia
using CSV, Tables, DataFrames

# DataFrame を csv ファイルに書き出す
df = DataFrame(rand(10, 10), :auto)
CSV.write("data.csv", df)

# 行列をメモリ内の IOBuffer に書き込む
io = IOBuffer()
mat = rand(10, 10)
CSV.write(io, Tables.table(mat))
```
