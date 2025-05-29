```
case_when(condition => return_value)
case_when(condition_1 => return_value_1, condition_2 => return_value_2, ...)
```

Return the corresponding `return_value` for the first `condition` that evaluates to `true`.

The most specific condition should be listed first and most general condition should be listed last. If none of the conditions evaluate to `true`, then a `missing` value is returned. 

# Arguments

  * `condition`: A condition that evaluates to `true`, `false`, or `missing`.
  * `return_value`: The value to return if the condition is `true`.

# Examples

```jldoctest
julia> df = DataFrame(a = [1, 2, missing, 4, 5]);

julia> @chain df begin
         @mutate(b = case_when(a > 4  =>  "hi",
                               a > 2  =>  "medium",
                               a > 0  =>  "low"))
       end
5×2 DataFrame
 Row │ a        b       
     │ Int64?   String? 
─────┼──────────────────
   1 │       1  low
   2 │       2  low
   3 │ missing  missing 
   4 │       4  medium
   5 │       5  hi

julia> @chain df begin
         @mutate(b = case_when(a > 4  =>  "hi",
                               a > 2  =>  "medium",
                               a > 0  =>  "low",
                               true   =>  "unknown"))
       end
5×2 DataFrame
 Row │ a        b       
     │ Int64?   String  
─────┼──────────────────
   1 │       1  low
   2 │       2  low
   3 │ missing  unknown
   4 │       4  medium
   5 │       5  hi

julia> @chain df begin
         @mutate(b = case_when(a >= 3  =>  3,
                               true    =>  a))
       end
5×2 DataFrame
 Row │ a        b       
     │ Int64?   Int64?  
─────┼──────────────────
   1 │       1        1
   2 │       2        2
   3 │ missing  missing 
   4 │       4        3
   5 │       5        3

julia> @chain df begin
         @mutate(b = case_when(a >= 3        =>  3,
                               ismissing(a)  =>  0,
                               true          =>  a))
       end
5×2 DataFrame
 Row │ a        b     
     │ Int64?   Int64 
─────┼────────────────
   1 │       1      1
   2 │       2      2
   3 │ missing      0
   4 │       4      3
   5 │       5      3
```
