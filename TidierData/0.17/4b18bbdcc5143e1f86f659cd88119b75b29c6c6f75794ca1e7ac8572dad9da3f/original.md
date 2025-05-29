```
if_else(condition, yes, no, [miss])
```

Return the `yes` value if the `condition` is `true` and the `no` value if the `condition` is `false`. If `miss` is specified, then the provided `miss` value is returned when the `condition` contains a `missing` value. If `miss` is not specified, then the returned value is an explicit `missing` value.

# Arguments

  * `condition`: A condition that evaluates to `true`, `false`, or `missing`.
  * `yes`: Value to return if the condition is `true`.
  * `no`: Value to return if the condition is `false`.
  * `miss`: Optional. Value to return if the condition is `missing`.

# Examples

```jldoctest
julia> df = DataFrame(a = [1, 2, missing, 4, 5]);

julia> @chain df begin
         @mutate(b = if_else(a >= 3, "yes", "no"))
       end
5×2 DataFrame
 Row │ a        b       
     │ Int64?   String? 
─────┼──────────────────
   1 │       1  no
   2 │       2  no
   3 │ missing  missing 
   4 │       4  yes
   5 │       5  yes

julia> @chain df begin
         @mutate(b = if_else(a >= 3, "yes", "no", "unknown"))
       end
5×2 DataFrame
 Row │ a        b       
     │ Int64?   String  
─────┼──────────────────
   1 │       1  no
   2 │       2  no
   3 │ missing  unknown
   4 │       4  yes
   5 │       5  yes

julia> @chain df begin
         @mutate(b = if_else(a >= 3, 3, a))
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
         @mutate(b = if_else(a >= 3, 3, a, 0))
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
