```
write_xlsx(x; path, overwrite)
```

DataFrameまたは複数のDataFrameをExcelファイルに書き込みます。各データフレームに対して特定のシートを指定できます。

# 引数

  * `x`: 書き込むデータ。1つのシートを書くための単一のPair{String, DataFrame}、または複数のシートを書くためのそのようなペアのタプルであることができます。各ペアのStringはシート名を指定し、DataFrameはそのシートに書き込むデータです。
  * `path`: データが書き込まれるExcelファイルのパス。
  * `overwrite`: デフォルトはfalseです。既存のファイルを上書きするかどうか。falseの場合、既存のファイルに書き込もうとするとエラーが発生します。

# 例

```jldoctest
julia> df = DataFrame(integers=[1, 2, 3, 4],
       strings=["This", "Package makes", "File reading/writing", "even smoother"],
       floats=[10.2, 20.3, 30.4, 40.5]);

julia> df2 = DataFrame(AA=["aa", "bb"], AB=[10.1, 10.2]);

julia> write_xlsx(("REPORT_A" => df, "REPORT_B" => df2); path="xlsxtest.xlsx", overwrite = true);
```
