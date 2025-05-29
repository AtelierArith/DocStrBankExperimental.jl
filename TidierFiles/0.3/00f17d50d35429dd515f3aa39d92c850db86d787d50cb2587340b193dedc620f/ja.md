```
write_tsv(DataFrame, filepath; na = "", append = false, col_names = true, missing_value, eol = "
```

", num_threads = Threads.nthreads()) DataFrameをTSV（タブ区切り値）ファイルに書き込みます。

# 引数

  * `x`: TSVファイルに書き込むDataFrame。
  * `file`: 出力TSVファイルのパス。
  * `missing_value`: = "": 出力ファイルで欠損値を表す文字列。デフォルトは空文字列です。
  * `append`: 既にファイルが存在する場合にファイルに追加するかどうか。デフォルトはfalseです。
  * `col_names`: = true: ファイルの最初の行に列名を書き込むかどうか。デフォルトはtrueです。
  * `eol`: 出力ファイルで使用する行末文字。デフォルトは改行文字です。
  * `num_threads` = Threads.nthreads(): ファイルを書き込むために使用するスレッドの数。デフォルトは利用可能なスレッドの数です。

# 例

```jldoctest
julia> df = DataFrame(ID = 1:5, Name = ["Alice", "Bob", "Charlie", "David", "Eva"], Score = [88, 92, 77, 85, 95]);

julia> write_tsv(df, "tsvtest.tsv");
```
