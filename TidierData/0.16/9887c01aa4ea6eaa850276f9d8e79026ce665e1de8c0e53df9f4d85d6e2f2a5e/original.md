```
@slice_max(df, column; with_ties = true, n, prop, missing_rm = true)
```

Retrieve rows with the maximum value(s) from the specified column of a DataFrame or GroupedDataFrame.

# Arguments

  * `df`: The source data frame or grouped data frame from which to slice rows.
  * `column`: The column for which to slice the maximum values.
  * `with_ties`: Whether or not all ties will be shown, defaults to true. When false it will only show the first row.
  * `prop`: The proportion of rows to slice.
  * `n`: An optional integer argument to specify the number of maximum rows to retrieve. If with_ties = true, and the ties > n, n will be overridden.
  * `missing_rm`: Defaults to true, skips the missing values when determining the proportion of the dataframe to slice.

# Examples

```jldoctest
julia> df = DataFrame(
           a = [missing, 0.2, missing, missing, 1, missing, 5, 6],
           b = [0.3, 2, missing, 3, 6, 5, 7, 7],
           c = [0.2, 0.2, 0.2, missing, 1, missing, 5, 6]);

julia> @chain df begin
         @slice_max(b)
       end 
2×3 DataFrame
 Row │ a         b         c        
     │ Float64?  Float64?  Float64? 
─────┼──────────────────────────────
   1 │      5.0       7.0       5.0
   2 │      6.0       7.0       6.0

julia> @chain df begin
         @slice_max(b, with_ties = false)
       end 
1×3 DataFrame
 Row │ a         b         c        
     │ Float64?  Float64?  Float64? 
─────┼──────────────────────────────
   1 │      5.0       7.0       5.0

julia> @chain df begin
         @slice_max(b, n = 3)
       end 
3×3 DataFrame
 Row │ a         b         c        
     │ Float64?  Float64?  Float64? 
─────┼──────────────────────────────
   1 │      5.0       7.0       5.0
   2 │      6.0       7.0       6.0
   3 │      1.0       6.0       1.0
   
julia> @chain df begin
         @slice_max(b, prop = 0.5, missing_rm = true)
       end
3×3 DataFrame
 Row │ a         b         c        
     │ Float64?  Float64?  Float64? 
─────┼──────────────────────────────
   1 │      5.0       7.0       5.0
   2 │      6.0       7.0       6.0
   3 │      1.0       6.0       1.0
```
