```
@rename(df, exprs...)
```

Change the names of individual column names in a DataFrame. Users can also use `@select()` to rename and select columns.

# Arguments

  * `df`: A DataFrame.
  * `exprs...`: Use `new_name = old_name` syntax to rename selected columns.

# Examples

```jldoctest
julia> df = DataFrame(a = 'a':'e', b = 1:5, c = 11:15);

julia> @chain df begin
         @rename(d = b, e = c)
       end
5×3 DataFrame
 Row │ a     d      e     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ b         2     12
   3 │ c         3     13
   4 │ d         4     14
   5 │ e         5     15
```
