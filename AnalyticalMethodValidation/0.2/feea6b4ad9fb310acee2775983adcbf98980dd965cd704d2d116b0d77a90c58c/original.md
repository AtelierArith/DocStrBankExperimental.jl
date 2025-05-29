```
selectby(df::DataFrame, col, col_pairs...; 
        pivot = false, 
        rows = [], 
        notsort = ["Stats", "File"], 
        prefix = true, 
        drop = [], 
        kwargs...)
```

Select values by `col`, and apply `select!` as if the values are columns.

# Arguments

  * `df`: target `DataFrame`.
  * `col`: column name.
  * `col_pairs`: `DataFrames.jl` syntax to manipulate columns. They will be put in internal `select!` function.

# Keyword Arguments

  * `rows`: the column(s) (Symbol, String, or Vector) preserving as row keys.
  * `pivot`: whether pivot the dataframe by `col`.
  * `notsort`: columns (Vector); do not sort by these columns.
  * `drop`: columns (Vector); drop these columns.
  * `kwargs`: keyword arguments for internal `select!` function.
