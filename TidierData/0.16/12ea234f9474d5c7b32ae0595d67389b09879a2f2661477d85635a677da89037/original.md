```
@count(df, exprs..., [wt], [sort])
```

Count the unique values of one or more variables, with an optional weighting.

`@chain df @count(a, b)` is roughly equivalent to `@chain df @group_by(a, b) @summarize(n = n())`. Supply `wt` to perform weighted counts, switching the summary from `n = n()` to `n = sum(wt)`. Note that if grouping columns are provided, the result will be an ungrouped data frame, which is slightly different behavior than R's `tidyverse`.

# Arguments

  * `df`: A DataFrame or GroupedDataFrame.
  * `exprs...`: Column names, separated by commas.
  * `wt`: Optional parameter. Used to calculate a sum over the provided `wt` variable instead of counting the rows.
  * `sort`: Defaults to `false`. Whether the result should be sorted from highest to lowest `n`.

# Examples

```jldoctest
julia> df = DataFrame(a = vcat(repeat(["a"], inner = 3),
                           repeat(["b"], inner = 3),
                           repeat(["c"], inner = 1),
                           missing),
                      b = 1:8)
8×2 DataFrame
 Row │ a        b     
     │ String?  Int64 
─────┼────────────────
   1 │ a            1
   2 │ a            2
   3 │ a            3
   4 │ b            4
   5 │ b            5
   6 │ b            6
   7 │ c            7
   8 │ missing      8

julia> @chain df @count()
1×1 DataFrame
 Row │ n     
     │ Int64 
─────┼───────
   1 │     8

julia> @chain df begin
         @count(a)
       end
4×2 DataFrame
 Row │ a        n     
     │ String?  Int64 
─────┼────────────────
   1 │ a            3
   2 │ b            3
   3 │ c            1
   4 │ missing      1

julia> @chain df begin
         @count(a, wt = b)
       end
4×2 DataFrame
 Row │ a        n     
     │ String?  Int64 
─────┼────────────────
   1 │ a            6
   2 │ b           15
   3 │ c            7
   4 │ missing      8

julia> @chain df begin
         @count(a, wt = b, sort = true)
       end
4×2 DataFrame
 Row │ a        n     
     │ String?  Int64 
─────┼────────────────
   1 │ b           15
   2 │ missing      8
   3 │ c            7
   4 │ a            6       
```
