From Excel Number Format to Date

```
	Date=fromExcelNumberToDate(ExcelNumber)
```

Where:

```
	ExcelNumber = Integer representing a date in the excel format.

	Date      = Date representing the input in the Julia object format.
```

# Example

```julia-repl
julia> fromExcelNumberToDate(45000)
2023-03-15
```
