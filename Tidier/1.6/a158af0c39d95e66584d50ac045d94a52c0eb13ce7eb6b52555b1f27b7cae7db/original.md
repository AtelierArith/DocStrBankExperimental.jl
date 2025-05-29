```
@filter(df, exprs...)
```

Subset a DataFrame and return a copy of DataFrame where specified conditions are satisfied.

# Arguments

  * `df`: A DataFrame.
  * `exprs...`: transformation(s) that produce vectors containing `true` or `false`.

# Examples

```jldoctest
julia> df = DataFrame(a = 'a':'e', b = 1:5, c = 11:15);

julia> @chain df begin
         @filter(b >= mean(b))
       end
3×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ c         3     13
   2 │ d         4     14
   3 │ e         5     15

julia> @chain df begin
         @filter(b >= 3 && c >= 14)
       end
2×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ d         4     14
   2 │ e         5     15

julia> @chain df begin
         @filter(b in (1, 3))
       end
2×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ c         3     13
```

```
@filter(sql_query, conditions...)
```

Filter rows in a SQL table based on specified conditions.

# Arguments

  * `sql_query::SQLQuery`: The SQL query to filter rows from.
  * `conditions`: Expressions specifying the conditions that rows must satisfy to be included in the output.                   Rows for which the expression evaluates to `true` will be included in the result.                   Multiple conditions can be combined using logical operators (`&&`, `||`). `@filter` will automatically                   detect whether the conditions belong in WHERE vs HAVING.

Temporarily, it is best to use begin and end when filtering multiple conditions. (ex 2 below)

# Examples

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> @chain dt(db, df, "df_view") begin
         @filter(percent > .5)
         @collect
       end
5×4 DataFrame
 Row │ id      groups  value  percent 
     │ String  String  Int64  Float64 
─────┼────────────────────────────────
   1 │ AF      aa          1      0.6
   2 │ AG      bb          2      0.7
   3 │ AH      aa          3      0.8
   4 │ AI      bb          4      0.9
   5 │ AJ      aa          5      1.0

julia> @chain dt(db, df, "df_view") begin
         @group_by(groups)
         @summarise(mean = mean(percent))
         @filter begin 
           groups == "bb" || # logical operators can still be used like this
           mean > .5
         end
         @arrange(groups)
         @collect
       end
2×2 DataFrame
 Row │ groups  mean    
     │ String  Float64 
─────┼─────────────────
   1 │ aa          0.6
   2 │ bb          0.5

julia> q = @chain dt(db, df, "df_view") @summarize(mean = mean(value));

julia> @eval @chain dt(db, df, "df_view") begin
         @filter(value < $q) 
         @collect
       end
4×4 DataFrame
 Row │ id      groups  value  percent 
     │ String  String  Int64  Float64 
─────┼────────────────────────────────
   1 │ AA      bb          1      0.1
   2 │ AB      aa          2      0.2
   3 │ AF      aa          1      0.6
   4 │ AG      bb          2      0.7
```
