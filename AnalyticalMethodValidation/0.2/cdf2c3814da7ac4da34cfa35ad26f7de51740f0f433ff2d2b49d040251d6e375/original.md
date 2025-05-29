```
unpivot(df::DataFrame, col; rows = [], notsort = ["Stats", "File"], drop = [])
unpivot(df::DataFrame, cols::AbstractVector; rows = [], notsort = ["Stats", "File"], drop = [])
```

Transform `DataFrame` into wide format.

# Arguments

  * `df`: target `DataFrame`.
  * `col`: the column name (Symbol or String) in long format.
  * `cols`: the column(s) (Vector) in long format.

# Keyword Arguments

  * `rows`: the column(s) (Symbol, String, or Vector) preserving as row keys in long format.
  * `notsort`: columns (Vector); do not sort by these columns.
  * `drop`: columns (Vector); drop these columns.
