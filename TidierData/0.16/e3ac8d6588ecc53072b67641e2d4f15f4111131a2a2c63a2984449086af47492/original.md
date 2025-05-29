```
desc(col)
```

Orders the rows of a DataFrame column in descending order when used inside of `@arrange()`. This function should only be called inside of `@arrange()``.

# Arguments

  * `col`: An unquoted column name.

# Examples

```jldoctest
julia> df = DataFrame(a = repeat('a':'e', inner = 2), b = 1:10, c = 11:20);
  
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
