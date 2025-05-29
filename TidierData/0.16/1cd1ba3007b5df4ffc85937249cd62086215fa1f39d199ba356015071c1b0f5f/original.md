```
@transmute(df, exprs...)
```

Create a new DataFrame with only computed columns.

# Arguments

  * `df`: A DataFrame.
  * `exprs...`: add new columns or replace values of existed columns using        `new_variable = values` syntax.

# Examples

```jldoctest
julia> df = DataFrame(a = 'a':'e', b = 1:5, c = 11:15);

julia> @chain df begin
         @transmute(d = b + c)
       end
5×1 DataFrame
 Row │ d     
     │ Int64 
─────┼───────
   1 │    12
   2 │    14
   3 │    16
   4 │    18
   5 │    20
```
