```
@mutate(df, exprs...)
```

Create new columns as functions of existing columns. The results have the same number of rows as `df`.

# Arguments

  * `df`: A DataFrame.
  * `exprs...`: add new columns or replace values of existed columns using        `new_variable = values` syntax.

# Examples

```jldoctest
julia> df = DataFrame(a = 'a':'e', b = 1:5, c = 11:15);

julia> @chain df begin
         @mutate(d = b + c,
                 b_minus_mean_b = b - mean(b))
       end
5×5 DataFrame
 Row │ a     b      c      d      b_minus_mean_b 
     │ Char  Int64  Int64  Int64  Float64        
─────┼───────────────────────────────────────────
   1 │ a         1     11     12            -2.0
   2 │ b         2     12     14            -1.0
   3 │ c         3     13     16             0.0
   4 │ d         4     14     18             1.0
   5 │ e         5     15     20             2.0

julia> @chain df begin
         @mutate begin
           d = b + c
           b_minus_mean_b = b - mean(b)
         end
       end
5×5 DataFrame
 Row │ a     b      c      d      b_minus_mean_b 
     │ Char  Int64  Int64  Int64  Float64        
─────┼───────────────────────────────────────────
   1 │ a         1     11     12            -2.0
   2 │ b         2     12     14            -1.0
   3 │ c         3     13     16             0.0
   4 │ d         4     14     18             1.0
   5 │ e         5     15     20             2.0

julia> @chain df begin
         @mutate(d = b in (1,3))
       end
5×4 DataFrame
 Row │ a     b      c      d     
     │ Char  Int64  Int64  Bool  
─────┼───────────────────────────
   1 │ a         1     11   true
   2 │ b         2     12  false
   3 │ c         3     13   true
   4 │ d         4     14  false
   5 │ e         5     15  false

julia> @chain df begin
         @mutate(across((b, c), mean))
       end
5×5 DataFrame
 Row │ a     b      c      b_mean   c_mean  
     │ Char  Int64  Int64  Float64  Float64 
─────┼──────────────────────────────────────
   1 │ a         1     11      3.0     13.0
   2 │ b         2     12      3.0     13.0
   3 │ c         3     13      3.0     13.0
   4 │ d         4     14      3.0     13.0
   5 │ e         5     15      3.0     13.0

julia> @chain df begin
         @summarize(across(contains("b"), mean))
       end
1×1 DataFrame
 Row │ b_mean  
     │ Float64 
─────┼─────────
   1 │     3.0

julia> @chain df begin
         @summarize(across(-contains("a"), mean))
       end
1×2 DataFrame
 Row │ b_mean   c_mean  
     │ Float64  Float64 
─────┼──────────────────
   1 │     3.0     13.0

julia> @chain df begin
         @mutate(across(where(is_number), minimum))
       end
5×5 DataFrame
 Row │ a     b      c      b_minimum  c_minimum 
     │ Char  Int64  Int64  Int64      Int64     
─────┼──────────────────────────────────────────
   1 │ a         1     11          1         11
   2 │ b         2     12          1         11
   3 │ c         3     13          1         11
   4 │ d         4     14          1         11
   5 │ e         5     15          1         11
```
