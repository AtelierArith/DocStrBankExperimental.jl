```
DataFrame(values::CellRangeValues)::Union{Nothing,DataFrame}
```

Creates a DataFrame from spreadsheet range values.  The first row is converted to column names.  All other rows are converted to string values.

# Arguments

  * `values::CellRangeValues`: cell values
