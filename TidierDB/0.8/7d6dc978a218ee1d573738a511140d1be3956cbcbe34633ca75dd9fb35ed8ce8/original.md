```
@head(sql_query, value)
```

Limit SQL table number of rows returned based on specified value.  `LIMIT` in SQL

# Arguments

  * `sql_query`: The SQL query to operate on.
  * `value`: Number to limit how many rows are returned. If left empty, it will default to 6 rows

# Examples

```jldoctest
julia> db = connect(duckdb());

julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);
                     

julia> @chain dt(db, df, "df_view") begin
        @head(1) ## supports expressions ie `3-2` would return the same df below
        @collect
       end
1×4 DataFrame
 Row │ id      groups  value  percent 
     │ String  String  Int64  Float64 
─────┼────────────────────────────────
   1 │ AA      bb          1      0.1
```
