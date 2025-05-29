```
@arrange(df, exprs...)
```

Order the rows of a DataFrame by the values of specified columns.

# Arguments

  * `df`: A DataFrame.
  * `exprs...`: Variables from the input DataFrame. Use `desc()` to sort in descending order. Multiple variables can be specified, separated by commas.

# Examples

```jldoctest
julia> df = DataFrame(a = repeat('a':'e', inner = 2), b = 1:10, c = 11:20);
  
julia> @chain df begin
         @arrange(a)
       end
10×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ a         2     12
   3 │ b         3     13
   4 │ b         4     14
   5 │ c         5     15
   6 │ c         6     16
   7 │ d         7     17
   8 │ d         8     18
   9 │ e         9     19
  10 │ e        10     20

julia> @chain df begin
         @arrange(a, desc(b))
       end
10×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         2     12
   2 │ a         1     11
   3 │ b         4     14
   4 │ b         3     13
   5 │ c         6     16
   6 │ c         5     15
   7 │ d         8     18
   8 │ d         7     17
   9 │ e        10     20
  10 │ e         9     19
```
