```
@summarize(df, exprs...)
@summarise(df, exprs...)
```

Create a new DataFrame with one row that aggregating all observations from the input DataFrame or GroupedDataFrame. 

# Arguments

  * `df`: A DataFrame.
  * `exprs...`: a `new_variable = function(old_variable)` pair. `function()` should be an aggregate function that returns a single value.

# Examples

```jldoctest
julia> df = DataFrame(a = 'a':'e', b = 1:5, c = 11:15);

julia> @chain df begin
         @summarize(mean_b = mean(b),
                    median_b = median(b))
       end
1×2 DataFrame
 Row │ mean_b   median_b 
     │ Float64  Float64  
─────┼───────────────────
   1 │     3.0       3.0

julia> @chain df begin
         @summarize begin
           mean_b = mean(b)
           median_b = median(b)
         end
       end
1×2 DataFrame
 Row │ mean_b   median_b 
     │ Float64  Float64  
─────┼───────────────────
   1 │     3.0       3.0 

julia> @chain df begin
         @summarise(mean_b = mean(b), median_b = median(b))
       end
1×2 DataFrame
 Row │ mean_b   median_b 
     │ Float64  Float64  
─────┼───────────────────
   1 │     3.0       3.0
   
julia> @chain df begin
         @summarize(across((b,c), (minimum, maximum)))
       end
1×4 DataFrame
 Row │ b_minimum  c_minimum  b_maximum  c_maximum 
     │ Int64      Int64      Int64      Int64     
─────┼────────────────────────────────────────────
   1 │         1         11          5         15

julia> @chain df begin
         @summarize(across(where(is_number), minimum))
       end
1×2 DataFrame
 Row │ b_minimum  c_minimum 
     │ Int64      Int64     
─────┼──────────────────────
   1 │         1         11
```

```
   @summarize(sql_query, exprs...; _by)
```

Aggregate and summarize specified columns of a SQL table.

# Arguments

  * `sql_query::SQLQuery`: The SQL query to summarize
  * `exprs`: Expressions defining the aggregation and summarization operations. These can specify simple aggregations like mean, sum, and count, or more complex expressions involving existing column values.
  * `_by`: optional argument that supports single column names, or vectors of columns to allow for grouping for the aggregatation in the macro call

# Examples

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> @chain dt(db, df, "df_view") begin
         @group_by(groups)
         @summarise(across((ends_with("e"), starts_with("p")), (mean, sum)))
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

julia> @chain dt(db, df, "df_view") begin
                @summarise(test = sum(percent), n = n(), _by = groups)
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
