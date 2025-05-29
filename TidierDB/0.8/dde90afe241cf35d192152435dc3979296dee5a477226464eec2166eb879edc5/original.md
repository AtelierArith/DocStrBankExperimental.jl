```
@count(sql_query, columns...)
```

Count the number of rows grouped by specified column(s).

# Arguments

  * `sql_query::SQLQuery`: The SQL query to operate on.
  * `columns`: Columns to group by before counting. If no columns are specified, counts all rows in the query.

# Examples

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());

julia> @chain dt(db, df, "df_view") begin
         @count(groups)
         @arrange(groups)
         @collect
       end
2×2 DataFrame
 Row │ groups  n     
     │ String  Int64 
─────┼───────────────
   1 │ aa          5
   2 │ bb          5
```
