```
@relocate(sql_query, columns, before = nothing, after = nothing)
```

Rearranges the columns in the queried table. This function allows for moving specified columns to a new position within the table, either before or after a given target column. The `columns`, `before`, and `after` arguments all accept tidy selection functions. Only one of `before` or `after` should be specified. If neither are specified, the selected columns will be moved to the beginning of the table.

# Arguments

  * `sql_query`: The SQL query
  * `columns`: Column or columns to to be moved.
  * `before`: (Optional) Column or columns before which the specified columns will be moved. If not provided or `nothing`, this argument is ignored.
  * `after`: (Optional) Column or columns after which the specified columns will be moved. If not provided or `nothing`, this argument is ignored.

# Examples

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> @chain dt(db, df, "df_view") begin 
        @relocate(groups, value, ends_with("d"), after = percent) 
        @collect
       end
10×4 DataFrame
 Row │ percent  groups  value  id     
     │ Float64  String  Int64  String 
─────┼────────────────────────────────
   1 │     0.1  bb          1  AA
   2 │     0.2  aa          2  AB
   3 │     0.3  bb          3  AC
   4 │     0.4  aa          4  AD
   5 │     0.5  bb          5  AE
   6 │     0.6  aa          1  AF
   7 │     0.7  bb          2  AG
   8 │     0.8  aa          3  AH
   9 │     0.9  bb          4  AI
  10 │     1.0  aa          5  AJ

julia> @chain dt(db, df, "df_view") begin 
        @relocate([:percent, :groups], before = id) 
        @collect
       end
10×4 DataFrame
 Row │ percent  groups  id      value 
     │ Float64  String  String  Int64 
─────┼────────────────────────────────
   1 │     0.1  bb      AA          1
   2 │     0.2  aa      AB          2
   3 │     0.3  bb      AC          3
   4 │     0.4  aa      AD          4
   5 │     0.5  bb      AE          5
   6 │     0.6  aa      AF          1
   7 │     0.7  bb      AG          2
   8 │     0.8  aa      AH          3
   9 │     0.9  bb      AI          4
  10 │     1.0  aa      AJ          5
```
