```
  @unite(df, new_cols, from_cols, sep, remove = true)
```

Separate a multiple columns into one new columns using a specific delimter

# Arguments

  * `df`: A DataFrame
  * `new_col`: New column that will recieve the combination
  * `from_cols`: Column names that it will combine, supports [] or ()
  * `sep`: the string or character that will separate the values in the new column
  * `remove`: defaults to `true`, removes input columns from data frame

# Examples

```jldoctest
julia> df = DataFrame( b = ["1", "2", "3"], c = ["1", "2", "3"], d = [missing, missing, "3"]);

julia> @unite(df, new_col, (b, c, d), "-")
3×1 DataFrame
 Row │ new_col 
     │ String  
─────┼─────────
   1 │ 1-1
   2 │ 2-2
   3 │ 3-3-3
   
julia> @unite(df, new_col, (b, c, d), "-", remove = false)
3×4 DataFrame
 Row │ b       c       d        new_col 
     │ String  String  String?  String  
─────┼──────────────────────────────────
   1 │ 1       1       missing  1-1
   2 │ 2       2       missing  2-2
   3 │ 3       3       3        3-3-3
```
