```
read_parquet(path)
```

Parquetファイル（.parquet）をDataFrameに読み込みます。

# 引数

  * `path`: 読み込むパーケットファイルへのパスまたはパスのベクターまたはURL
  * `col_names`: CSVの最初の行が列名として使用されるかどうかを示します。true、false、または文字列の配列を指定できます。デフォルトはtrueです。
  * `skip`: データを読み込む前にスキップする初期行の数。デフォルトは0です。
  * `n_max`: 読み込む最大行数。デフォルトはInf（すべての行を読み込む）です。
  * `col_select`: 読み込む列を選択するためのオプションのシンボルまたは文字列のベクター。

# 例

```jldoctest
julia> df = DataFrame(AA=["Par", "quet"], AB=[10.1, 10.2]);

julia> write_parquet(df, "test.parquet");

julia> read_parquet("test.parquet")
2×2 DataFrame
 Row │ AA      AB      
     │ String  Float64 
─────┼─────────────────
   1 │ Par        10.1
   2 │ quet       10.2
```
