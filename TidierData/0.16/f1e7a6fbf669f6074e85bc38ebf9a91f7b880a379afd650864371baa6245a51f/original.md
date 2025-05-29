```
row_number()
```

Return each row's number in a DataFrame or in the group if used in the context of a GroupedDataFrame.

# Arguments

  * None

# Examples

```jldoctest
julia> df = DataFrame(a = repeat('a':'e', inner = 2));

julia> @chain df begin
         @mutate(row_num = row_number())
       end
10×2 DataFrame
 Row │ a     row_num 
     │ Char  Int64   
─────┼───────────────
   1 │ a           1
   2 │ a           2
   3 │ b           3
   4 │ b           4
   5 │ c           5
   6 │ c           6
   7 │ d           7
   8 │ d           8
   9 │ e           9
  10 │ e          10

julia> @chain df begin
         @mutate(row_num = row_number() + 1)
       end
10×2 DataFrame
 Row │ a     row_num 
     │ Char  Int64   
─────┼───────────────
   1 │ a           2
   2 │ a           3
   3 │ b           4
   4 │ b           5
   5 │ c           6
   6 │ c           7
   7 │ d           8
   8 │ d           9
   9 │ e          10
  10 │ e          11

julia> @chain df begin
         @filter(row_number() <= 5)
       end
5×1 DataFrame
 Row │ a    
     │ Char 
─────┼──────
   1 │ a
   2 │ a
   3 │ b
   4 │ b
   5 │ c
```
