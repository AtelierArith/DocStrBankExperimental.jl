```
  @unite(sql_query, new_cols, from_cols, sep, remove = true)
```

Separate a multiple columns into one new columns using a specific delimter

# Arguments

  * `sql_query`: The SQL query
  * `new_col`: New column that will recieve the combination
  * `from_cols`: Column names that it will combine, supports [] or ()
  * `sep`: the string or character that will separate the values in the new column

# Examples

```jldoctest
julia> db = connect(duckdb());

julia> df = DataFrame( b = ["1", "2", "3"], c = ["1", "2", "3"], d = [missing, missing, "3"]);

julia> @chain dt(db, df, "df") @unite(new_col, (b, c, d), "-") @collect
3×1 DataFrame
 Row │ new_col 
     │ String  
─────┼─────────
   1 │ 1-1
   2 │ 2-2
   3 │ 3-3-3
```
