```
read_xlsx(path; sheet, range, col_names, col_types, missing_value, trim_ws, skip, n_max, guess_max)
```

ExcelファイルからデータをDataFrameに読み込みます。

# 引数

  * `path`: 読み込むExcelファイルのパス。
  * `sheet`: 読み込むシートを指定します。シートの名前を文字列として指定するか、インデックスを整数として指定できます。何も指定しない場合、最初のシートが読み込まれます。
  * `range`: シートから読み込む特定のセルの範囲を指定します。何も指定しない場合、シート全体が読み込まれます。
  * `col_names`: 指定された範囲の最初の行を列名として扱うかどうかを示します。falseの場合、列は自動的に名前が付けられます。
  * `col_types`: 列の型を明示的に指定することができます。すべての列に適用される単一の型、列名またはインデックスを型にマッピングするリストまたは辞書を指定できます。何も指定しない場合、型は推測されます。
  * `missing_value`: Excelファイル内の欠損値を表す値またはベクトル。CSV.jlベースの関数とは異なり、すべてを文字列として書く必要はありません。
  * `trim_ws`: Excelファイル内のセルから前後の空白をトリムするかどうか。
  * `skip`: データを読み込む前にシートまたは範囲の先頭でスキップする行数。
  * `n_max`: スキップ後にシートまたは範囲から読み込む最大行数。Infは利用可能なすべての行を読み込むことを意味します。
  * `guess_max`: 型推測と列名検出のためにスキャンする最大行数。col*typesが何も指定されていないか、col*namesがtrueの場合にのみ関連します。何も指定しない場合、デフォルトのヒューリスティックが使用されます。

# 例

```jldoctest
julia> df = DataFrame(integers=[1, 2, 3, 4],
       strings=["This", "Package makes", "File reading/writing", "even smoother"],
       floats=[10.2, 20.3, 30.4, 40.5]);

julia> df2 = DataFrame(AA=["aa", "bb"], AB=[10.1, 10.2]);

julia> write_xlsx(("REPORT_A" => df, "REPORT_B" => df2); path="xlsxtest.xlsx", overwrite = true);

julia> read_xlsx("xlsxtest.xlsx", sheet = "REPORT_A", skip = 1, n_max = 4, missing_value = [2])
3×3 DataFrame
 Row │ integers  strings               floats   
     │ Int64?    String?               Float64? 
─────┼──────────────────────────────────────────
   1 │  missing  Package makes             20.3
   2 │        3  File reading/writing      30.4
   3 │        4  even smoother             40.5
```
