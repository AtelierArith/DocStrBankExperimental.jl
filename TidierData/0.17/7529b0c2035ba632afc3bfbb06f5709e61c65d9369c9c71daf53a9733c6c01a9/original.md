```
@slice_head(df; n, prop)
```

Retrieve rows from the beginning of a DataFrame or GroupedDataFrame.

# Arguments

  * `df`: The source data frame or grouped data frame from which to slice rows.
  * `prop`: The proportion of rows to slice.
  * `n`: An optional integer argument to specify the number of rows at the beginning of the dataframe to retrieve. Defaults to 1.

# Examples

```jldoctest
julia> df = DataFrame(
           a = ["a", "b", "a", "b", "a", "b", "a", "a"],
           b = [0.3, 2, missing, 0.3, 6, 5, 7, 7],
           c = [0.2, 0.2, 0.2, missing, 1, missing, 5, 6]);

julia> @chain df begin
         @slice_head(prop = .3)
       end 
2×3 DataFrame
 Row │ a       b         c        
     │ String  Float64?  Float64? 
─────┼────────────────────────────
   1 │ a            0.3       0.2
   2 │ b            2.0       0.2

julia> @chain df begin
         @group_by(a)
         @slice_head(n = 2)
         @ungroup
       end 
4×3 DataFrame
 Row │ a       b          c         
     │ String  Float64?   Float64?  
─────┼──────────────────────────────
   1 │ a             0.3        0.2
   2 │ a       missing          0.2
   3 │ b             2.0        0.2
   4 │ b             0.3  missing   
```
