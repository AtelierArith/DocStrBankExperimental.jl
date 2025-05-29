```
pivot(df::DataFrame, col; rows = [], prefix = true, notsort = ["Stats", "File"], drop = [])
pivot(df::DataFrame, cols::AbstractVector; rows = [], prefix = true, notsort = ["Stats", "File"], drop = [])
```

Transform `DataFrame` into wide format.

# Arguments

  * `df`: target `DataFrame`.
  * `col`: the column (Symbol or String) holding the column names in wide format.
  * `cols`: the column(s) (Vector) holding the column names in wide format.

# Keyword Arguments

  * `rows`: the column(s) (Symbol, String, or Vector) preserving as row keys in wide format.
  * `prefix`: whether preserving `col` or `cols` in column names.
  * `notsort`: columns (Vector); do not sort by these columns.
  * `drop`: columns (Vector); drop these columns.
