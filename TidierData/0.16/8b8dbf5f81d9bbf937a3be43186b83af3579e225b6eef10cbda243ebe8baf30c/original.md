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
