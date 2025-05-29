```
@distinct(sql_query, columns...)
```

Select distinct rows based on specified column(s). Distinct works differently in TidierData vs SQL and therefore TidierDB. Distinct will also select only the only columns it is given (or all if given none)

# Arguments

`sql_query::SQLQuery`: The SQL query to operate on. `columns`: Columns to determine uniqueness. If no columns are specified, all columns are used to identify distinct rows.

# Examples

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> @chain dt(db, df, "df_view") begin
         @distinct(value)
         @arrange(value)
         @collect
       end
5×1 DataFrame
 Row │ value 
     │ Int64 
─────┼───────
   1 │     1
   2 │     2
   3 │     3
   4 │     4
   5 │     5

julia> @chain dt(db, df, "df_view") begin
         @distinct
         @arrange(id)
         @collect
       end
10×4 DataFrame
 Row │ id      groups  value  percent 
     │ String  String  Int64  Float64 
─────┼────────────────────────────────
   1 │ AA      bb          1      0.1
   2 │ AB      aa          2      0.2
   3 │ AC      bb          3      0.3
   4 │ AD      aa          4      0.4
   5 │ AE      bb          5      0.5
   6 │ AF      aa          1      0.6
   7 │ AG      bb          2      0.7
   8 │ AH      aa          3      0.8
   9 │ AI      bb          4      0.9
  10 │ AJ      aa          5      1.0
```
