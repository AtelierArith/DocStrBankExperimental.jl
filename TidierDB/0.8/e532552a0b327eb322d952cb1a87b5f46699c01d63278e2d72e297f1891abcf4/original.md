```
@slice_max(sql_query, column, n = 1)
```

Select rows with the largest values in specified column. This will always return ties. 

# Arguments

  * `sql_query::SQLQuery`: The SQL query to operate on.
  * `column`: Column to identify the smallest values.
  * `n`: The number of rows to select with the largest values for each specified column. Default is 1, which selects the row with the smallest value.

# Examples

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> @chain dt(db, df, "df_view") begin
         @group_by(groups)
         @slice_max(value, n = 2)
         @arrange(groups)
         @collect
       end
4×5 DataFrame
 Row │ id      groups  value  percent  rank_col 
     │ String  String  Int64  Float64  Int64    
─────┼──────────────────────────────────────────
   1 │ AJ      aa          5      1.0         1
   2 │ AD      aa          4      0.4         2
   3 │ AE      bb          5      0.5         1
   4 │ AI      bb          4      0.9         2

julia> @chain dt(db, df, "df_view") begin
         @slice_max(value)
         @collect
       end
2×5 DataFrame
 Row │ id      groups  value  percent  rank_col 
     │ String  String  Int64  Float64  Int64    
─────┼──────────────────────────────────────────
   1 │ AE      bb          5      0.5         1
   2 │ AJ      aa          5      1.0         1

julia> @chain dt(db, df, "df_view") begin
        @filter(percent < .9)
        @slice_max(percent)
        @collect
       end
1×5 DataFrame
 Row │ id      groups  value  percent  rank_col 
     │ String  String  Int64  Float64  Int64    
─────┼──────────────────────────────────────────
   1 │ AH      aa          3      0.8         1

julia>  @chain dt(db, df, "df_view") begin
         @group_by groups
         @slice_max(percent)
         @arrange groups
         @collect
       end
2×5 DataFrame
 Row │ id      groups  value  percent  rank_col 
     │ String  String  Int64  Float64  Int64    
─────┼──────────────────────────────────────────
   1 │ AJ      aa          5      1.0         1
   2 │ AI      bb          4      0.9         1

julia> @chain dt(db, df, "df_view") begin
         @summarize(percent_mean = mean(percent), _by = groups)
         @slice_max(percent_mean)
         @collect
       end
1×3 DataFrame
 Row │ groups  percent_mean  rank_col 
     │ String  Float64       Int64    
─────┼────────────────────────────────
   1 │ aa               0.6         1
```
