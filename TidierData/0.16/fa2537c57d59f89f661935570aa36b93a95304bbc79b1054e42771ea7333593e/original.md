```
distinct(df, exprs...)
```

Return distinct rows of a DataFrame.

If no columns or expressions are provided, then unique rows across all columns are returned. Otherwise, unique rows are determined based on the columns or expressions provided, and then all columns are returned.

# Arguments

  * `df`: A DataFrame.
  * `exprs...`: One or more unquoted variable names separated by commas. Variable names         can also be used as their positions in the data, like `x:y`, to select         a range of variables.

# Examples

```jldoctest
julia> df = DataFrame(a = repeat('a':'e', inner = 2), b = repeat(1:5, 2), c = 11:20);
  
julia> @chain df @distinct()
10×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ a         2     12
   3 │ b         3     13
   4 │ b         4     14
   5 │ c         5     15
   6 │ c         1     16
   7 │ d         2     17
   8 │ d         3     18
   9 │ e         4     19
  10 │ e         5     20

julia> @chain df @distinct(a)
5×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ b         3     13
   3 │ c         5     15
   4 │ d         2     17
   5 │ e         4     19

julia> @chain df begin
         @distinct(starts_with("a"))
       end
5×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ b         3     13
   3 │ c         5     15
   4 │ d         2     17
   5 │ e         4     19

julia> @chain df begin
         @distinct(a, b)
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
   6 │ c         1     16
   7 │ d         2     17
   8 │ d         3     18
   9 │ e         4     19
  10 │ e         5     20
```
