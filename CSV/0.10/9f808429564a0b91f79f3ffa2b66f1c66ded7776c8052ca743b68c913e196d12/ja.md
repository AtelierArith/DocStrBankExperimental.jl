CSVは、さまざまな形式の区切りテキストファイルのための高速で柔軟なリーダーおよびライターを提供します。

読み取り:

  * `CSV.File`は区切りデータを読み取り、列へのドットアクセスと行の反復を可能にする`CSV.File`オブジェクトを返します。
  * `CSV.read`は`CSV.File`に似ていますが、入力が`DataFrame`などのシンク関数に直接渡される場合に使用されます。
  * `CSV.Rows`は区切りデータを読み取り、データを反復することによって「ストリーミング」することを可能にする`CSV.Rows`オブジェクトを返し、`CSV.File`よりも低いメモリフットプリントを持ちます。
  * `CSV.Chunks`は、非常に大きなファイルを「バッチ」または「チャンク」で処理することを可能にします。

書き込み:

  * `CSV.write`は、`DataFrame`のような[Tables.jlインターフェース入力](https://github.com/JuliaData/Tables.jl)をcsvファイルまたはメモリ内のIOBufferに書き込みます。
  * `CSV.RowWriter`は、入力テーブルの各行に対してcsv形式の文字列を生成するイテレータを作成します。

以下は、csvファイルを読み取り、入力を`DataFrame`に渡す例です：

```julia
using CSV, DataFrames
ExampleInputDF = CSV.read("ExampleInputFile.csv", DataFrame)
```

以下は、`DataFrame`をcsvファイルに書き出す例です：

```julia
using CSV, DataFrames
ExampleOutputDF = DataFrame(rand(10,10), :auto)
CSV.write("ExampleOutputFile.csv", ExampleOutputDF)
```
