```
@group_by(df, exprs...)
```

Return a `GroupedDataFrame` where operations are performed by groups specified by unique  sets of `cols`.

# Arguments

  * `df`: A DataFrame.
  * `exprs...`: DataFrame columns to group by or tidy expressions. Can be a single tidy expression or multiple expressions separated by commas.

# Examples

```jldoctest
julia> df = DataFrame(a = 'a':'e', b = 1:5, c = 11:15);

julia> @chain df begin
         @group_by(a)
         @summarize(b = mean(b))
       end
5×2 DataFrame
 Row │ a     b       
     │ Char  Float64 
─────┼───────────────
   1 │ a         1.0
   2 │ b         2.0
   3 │ c         3.0
   4 │ d         4.0
   5 │ e         5.0  

julia> @chain df begin
         @group_by(d = uppercase(a))
         @summarize(b = mean(b))
       end
5×2 DataFrame
 Row │ d     b       
     │ Char  Float64 
─────┼───────────────
   1 │ A         1.0
   2 │ B         2.0
   3 │ C         3.0
   4 │ D         4.0
   5 │ E         5.0

julia> @chain df begin
         @group_by(-(b, c)) # same as `a`
         @summarize(b = mean(b))
       end
5×2 DataFrame
 Row │ a     b       
     │ Char  Float64 
─────┼───────────────
   1 │ a         1.0
   2 │ b         2.0
   3 │ c         3.0
   4 │ d         4.0
   5 │ e         5.0

julia> @chain df begin
         @group_by(!(b, c)) # same as `a`
         @summarize(b = mean(b))
       end
5×2 DataFrame
 Row │ a     b       
     │ Char  Float64 
─────┼───────────────
   1 │ a         1.0
   2 │ b         2.0
   3 │ c         3.0
   4 │ d         4.0
   5 │ e         5.0
```

```
@group_by(sql_query, columns...)
```

Group SQL table rows by specified column(s). If grouping is performed as a terminal operation without a  subsequent mutatation or summarization (as in the example below), then the resulting data frame will only  contains those groups. Collecting following a grouping will not return a grouped dataframe as TidierData does. 

# Arguments

  * `sql_query`: The SQL query to operate on.
  * `exprs`: Expressions specifying the columns to group by. Columns can be specified by name.

# Examples

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());

julia> @chain dt(db, df, "df_view") begin
         @group_by(groups)
         @arrange(groups)
         @collect
       end
2×1 DataFrame
 Row │ groups 
     │ String 
─────┼────────
   1 │ aa
   2 │ bb

julia> @chain dt(db, df, "df_view") begin
         @group_by(big_val = if_else(value > 3, "big", "small"))
         @summarise(n=n())
         @arrange(big_val)
         @collect
       end
2×2 DataFrame
 Row │ big_val  n     
     │ String   Int64 
─────┼────────────────
   1 │ big          4
   2 │ small        6
```
