```
@slice_min(sql_query, column, n = 1)
```

Select rows with the smallest values in specified column. This will always return ties. 

# Arguments

  * `sql_query::SQLQuery`: The SQL query to operate on.
  * `column`: Column to identify the smallest values.
  * `n`: The number of rows to select with the smallest values for each specified column. Default is 1, which selects the row with the smallest value.

# Examples

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> @chain dt(db, df, "df_view") begin
         @group_by(groups)
         @slice_min(value, n = 2)
         @arrange(groups, percent) # arranged due to duckdb multi threading
         @collect
       end
4×5 DataFrame
 Row │ id      groups  value  percent  rank_col 
     │ String  String  Int64  Float64  Int64    
─────┼──────────────────────────────────────────
   1 │ AB      aa          2      0.2         2
   2 │ AF      aa          1      0.6         1
   3 │ AA      bb          1      0.1         1
   4 │ AG      bb          2      0.7         2

julia> @chain dt(db, df, "df_view") begin
         @slice_min(value)
         @collect
       end
2×5 DataFrame
 Row │ id      groups  value  percent  rank_col 
     │ String  String  Int64  Float64  Int64    
─────┼──────────────────────────────────────────
   1 │ AA      bb          1      0.1         1
   2 │ AF      aa          1      0.6         1

julia> @chain dt(db, df, "df_view") begin
         @filter(percent > .1)
         @slice_min(percent)
         @collect
       end
1×5 DataFrame
 Row │ id      groups  value  percent  rank_col 
     │ String  String  Int64  Float64  Int64    
─────┼──────────────────────────────────────────
   1 │ AB      aa          2      0.2         1

julia> @chain dt(db, df, "df_view") begin
         @group_by groups
         @slice_min(percent)
         @arrange groups
         @collect
       end
2×5 DataFrame
 Row │ id      groups  value  percent  rank_col 
     │ String  String  Int64  Float64  Int64    
─────┼──────────────────────────────────────────
   1 │ AB      aa          2      0.2         1
   2 │ AA      bb          1      0.1         1

julia> @chain dt(db, df, "df_view") begin
         @summarize(percent_mean = mean(percent), _by = groups)
         @slice_min(percent_mean)
         @collect
       end
1×3 DataFrame
 Row │ groups  percent_mean  rank_col 
     │ String  Float64       Int64    
─────┼────────────────────────────────
   1 │ bb               0.5         1
```
