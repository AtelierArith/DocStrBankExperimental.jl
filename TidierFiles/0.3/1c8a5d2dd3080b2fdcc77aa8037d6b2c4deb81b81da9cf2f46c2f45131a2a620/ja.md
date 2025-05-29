```
read_arrow(df, path)
```

Arrowファイル（.arrow）をDataFrameに読み込みます。

# 引数

  * `df`: ファイルに書き込むDataFrame。
  * `path`: .dtaファイルが作成されるパスとしての文字列。このパスに既にファイルが存在する場合は上書きされます。
  * `skip`: データを読み込む前にスキップする初期行の数。デフォルトは0です。
  * `n_max`: 読み込む最大行数。デフォルトはInf（すべての行を読み込む）です。
  * `col_select`: 読み込む列を選択するためのオプションのシンボルまたは文字列のベクター。

# 例

```jldoctest
julia> df = DataFrame(AA=["Arr", "ow"], AB=[10.1, 10.2]);

julia> write_arrow(df , "test.arrow");

julia> read_arrow("test.arrow")
2×2 DataFrame
 Row │ AA      AB      
     │ String  Float64 
─────┼─────────────────
   1 │ Arr        10.1
   2 │ ow         10.2
```
