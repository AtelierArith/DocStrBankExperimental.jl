Excelの数値形式から日付へ

```
	Date=fromExcelNumberToDate(ExcelNumber)
```

ここで：

```
	ExcelNumber = Excel形式の日付を表す整数。

	Date      = Juliaオブジェクト形式での入力を表す日付。
```

# 例

```julia-repl
julia> fromExcelNumberToDate(45000)
2023-03-15
```
