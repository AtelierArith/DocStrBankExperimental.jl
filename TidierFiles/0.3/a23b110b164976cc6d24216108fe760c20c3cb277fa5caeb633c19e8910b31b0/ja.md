```
write_parquet(df, )
```

DataFrameをParquet（.parquet）ファイルに書き込みます。

# 引数

  * `df`: ファイルに書き込むDataFrame。
  * `path`: .dtaファイルが作成されるパスとしての文字列。このパスに既にファイルが存在する場合は上書きされます。

# 例

```jldoctest
julia> df = DataFrame(AA=["Par", "quet"], AB=[10.1, 10.2]);

julia> write_parquet(df, "test.parquet");
```
