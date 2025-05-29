```
@select(df, exprs...)
```

Select variables in a DataFrame.

# Arguments

  * `df`: A DataFrame.
  * `exprs...`: One or more unquoted variable names separated by commas. Variable names         can also be used as their positions in the data, like `x:y`, to select         a range of variables.

# Examples

```jldoctest
julia> df = DataFrame(a = 'a':'e', b = 1:5, c = 11:15);

julia> @chain df @select(a, b, c)
5×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ b         2     12
   3 │ c         3     13
   4 │ d         4     14
   5 │ e         5     15

julia> @chain df @select(a:b)
5×2 DataFrame
 Row │ a     b     
     │ Char  Int64 
─────┼─────────────
   1 │ a         1
   2 │ b         2
   3 │ c         3
   4 │ d         4
   5 │ e         5

julia> @chain df @select(1:2)
5×2 DataFrame
 Row │ a     b     
     │ Char  Int64 
─────┼─────────────
   1 │ a         1
   2 │ b         2
   3 │ c         3
   4 │ d         4
   5 │ e         5

julia> @chain df @select(-(a:b))
5×1 DataFrame
 Row │ c     
     │ Int64 
─────┼───────
   1 │    11
   2 │    12
   3 │    13
   4 │    14
   5 │    15

julia> @chain df @select(!(a:b))
5×1 DataFrame
 Row │ c     
     │ Int64 
─────┼───────
   1 │    11
   2 │    12
   3 │    13
   4 │    14
   5 │    15

julia> @chain df @select(-(a, b))
5×1 DataFrame
 Row │ c     
     │ Int64 
─────┼───────
   1 │    11
   2 │    12
   3 │    13
   4 │    14
   5 │    15

julia> @chain df @select(!(a, b))
5×1 DataFrame
 Row │ c     
     │ Int64 
─────┼───────
   1 │    11
   2 │    12
   3 │    13
   4 │    14
   5 │    15

julia> @chain df begin
         @select(contains("b"), starts_with("c"))
       end
5×2 DataFrame
 Row │ b      c     
     │ Int64  Int64 
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13
   4 │     4     14
   5 │     5     15

julia> @chain df @select(-(1:2))
5×1 DataFrame
 Row │ c     
     │ Int64 
─────┼───────
   1 │    11
   2 │    12
   3 │    13
   4 │    14
   5 │    15

julia> @chain df @select(!(1:2))
5×1 DataFrame
 Row │ c     
     │ Int64 
─────┼───────
   1 │    11
   2 │    12
   3 │    13
   4 │    14
   5 │    15

julia> @chain df @select(-c)
5×2 DataFrame
 Row │ a     b     
     │ Char  Int64 
─────┼─────────────
   1 │ a         1
   2 │ b         2
   3 │ c         3
   4 │ d         4
   5 │ e         5

julia> @chain df begin
         @select(-contains("a"))
       end
5×2 DataFrame
 Row │ b      c     
     │ Int64  Int64 
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13
   4 │     4     14
   5 │     5     15
   
julia> @chain df begin
         @select(!contains("a"))
       end
5×2 DataFrame
 Row │ b      c     
     │ Int64  Int64 
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13
   4 │     4     14
   5 │     5     15

julia> @chain df begin
         @select(where(is_number))
       end
5×2 DataFrame
 Row │ b      c     
     │ Int64  Int64 
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13
   4 │     4     14
   5 │     5     15
```
