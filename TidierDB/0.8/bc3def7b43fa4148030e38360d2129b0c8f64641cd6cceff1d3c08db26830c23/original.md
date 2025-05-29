```
   @summarise(sql_query, exprs...)
```

Aggregate and summarize specified columns of a SQL table.

# Arguments

  * `sql_query::SQLQuery`: query to be summarized
  * `exprs`: Expressions defining the aggregation and summarization operations.    These can specify simple aggregations like mean, sum, and count, ' or more complex expressions    involving existing column values. `@summarize`  supports all SQL database aggregate functions   as long as they are written with matching syntax

# Examples

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> @chain dt(db, df, "df_view") begin
         @group_by(groups)
         @summarise(across((value:percent), (mean, sum)))
         @arrange(groups)
         @collect
       end
2×5 DataFrame
 Row │ groups  value_mean  percent_mean  value_sum  percent_sum 
     │ String  Float64     Float64       Int128     Float64     
─────┼──────────────────────────────────────────────────────────
   1 │ aa             3.0           0.6         15          3.0
   2 │ bb             3.0           0.5         15          2.5

julia> @chain dt(db, df, "df_view") begin
         @group_by(groups)
         @summarise(test = sum(percent), n = n())
         @arrange(groups)
         @collect
       end
2×3 DataFrame
 Row │ groups  test     n     
     │ String  Float64  Int64 
─────┼────────────────────────
   1 │ aa          3.0      5
   2 │ bb          2.5      5
```
