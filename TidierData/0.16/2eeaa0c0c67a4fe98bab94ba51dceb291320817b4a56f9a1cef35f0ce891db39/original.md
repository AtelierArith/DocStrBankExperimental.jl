```
@slice_tail(df; n, prop)
```

Retrieve rows from the end of a DataFrame or GroupedDataFrame.

# Arguments

  * `df`: The source data frame or grouped data frame from which to slice rows.
  * `prop`: The proportion of rows to slice.
  * `n`: An optional integer argument to specify the number of rows at the beginning of the dataframe to retrieve. Defaults to 1.

# Examples

```jldoctest
julia> df = DataFrame(
           a = [missing, 0.2, missing, missing, 1, missing, 5, 6],
           b = [0.3, 2, missing, 0.3, 6, 5, 7, 7],
           c = [0.2, 0.2, 0.2, missing, 1, missing, 5, 6]);

julia> @chain df begin
         @slice_tail(n = 3)
       end 
3×3 DataFrame
 Row │ a          b         c         
     │ Float64?   Float64?  Float64?  
─────┼────────────────────────────────
   1 │ missing         5.0  missing   
   2 │       5.0       7.0        5.0
   3 │       6.0       7.0        6.0

julia> @chain df begin
         @slice_tail(prop = 0.25)
       end 
2×3 DataFrame
 Row │ a         b         c        
     │ Float64?  Float64?  Float64? 
─────┼──────────────────────────────
   1 │      5.0       7.0       5.0
   2 │      6.0       7.0       6.0
```
