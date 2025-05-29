```
write_dta(df, path)
```

DataFrameをStata（.dta）ファイルに書き込みます。

# 引数

  * `df`: ファイルに書き込むDataFrame。
  * `path`: .dtaファイルが作成されるパスとしての文字列。このパスに既にファイルが存在する場合は上書きされます。

# 例

```jldoctest
julia> df = DataFrame(AA=["sav", "por"], AB=[10.1, 10.2]);

julia> write_dta(df, "test.dta")
2×2 ReadStatTable:
 Row │     AA        AB 
     │ String  Float64? 
─────┼──────────────────
   1 │    sav      10.1
   2 │    por      10.2
```
