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
