@pivot*wider(df, names*from, values*from[, values*fill])

Reshapes the DataFrame to make it wider, increasing the number of columns and reducing the number of rows.

# Arguments

  * `df`: A DataFrame.
  * `names_from`: The name of the column to get the name of the output columns from.
  * `values_from`: The name of the column to get the cell values from.
  * `values_fill`: The value to replace a missing name/value combination (default is `missing`)

# Examples

```jldoctest
julia> df_long = DataFrame(id = [1, 1, 2, 2],
                           variable = ["A", "B", "A", "B"],
                           value = [1, 2, 3, 4]);

julia> df_long_missing = DataFrame(id = [1, 1, 2],
                           variable = ["A", "B", "B"],
                           value = [1, 2, 4]);

julia> @pivot_wider(df_long, names_from = variable, values_from = value)
2×3 DataFrame
 Row │ id     A       B      
     │ Int64  Int64?  Int64?
─────┼───────────────────────
   1 │     1       1       2
   2 │     2       3       4

julia> @pivot_wider(df_long, names_from = "variable", values_from = "value")
2×3 DataFrame
 Row │ id     A       B      
     │ Int64  Int64?  Int64?
─────┼───────────────────────
   1 │     1       1       2
   2 │     2       3       4

julia> @pivot_wider(df_long_missing, names_from = variable, values_from = value, values_fill = 0)
2×3 DataFrame
 Row │ id     A      B     
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      1      2
   2 │     2      0      4
```
