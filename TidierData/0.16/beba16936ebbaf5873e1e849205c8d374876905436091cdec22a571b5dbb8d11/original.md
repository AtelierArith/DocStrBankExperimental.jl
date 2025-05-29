```
@slice_min(df, column; with_ties = true, n, prop, missing_rm = true)
```

Retrieve rows with the minimum value(s) from the specified column of a DataFrame or GroupedDataFrame.

# Arguments

  * `df`: The source data frame or grouped data frame from which to slice rows.
  * `column`: The column for which to slice the minimum values.
  * `with_ties`: Whether or not all ties will be shown, defaults to true and shows all ties. When false it will only show the first row.
  * `prop`: The proportion of rows to slice.
  * `n`: An optional integer argument to specify the number of minimum rows to retrieve. If with_ties = true, and the ties > n, n will be overridden.
  * `missing_rm`: Defaults to true, skips the missing values when determining the proportion of the dataframe to slice.

# Examples

```jldoctest
julia> df = DataFrame(
           a = [missing, 0.2, missing, missing, 1, missing, 5, 6],
           b = [0.3, 2, missing, 0.3, 6, 5, 7, 7],
           c = [0.2, 0.2, 0.2, missing, 1, missing, 5, 6]);

julia> @chain df begin
         @slice_min(b)
       end 
2×3 DataFrame
 Row │ a         b         c         
     │ Float64?  Float64?  Float64?  
─────┼───────────────────────────────
   1 │  missing       0.3        0.2
   2 │  missing       0.3  missing

julia> @chain df begin
         @slice_min(b, with_ties = false)
       end 
1×3 DataFrame
 Row │ a         b         c        
     │ Float64?  Float64?  Float64? 
─────┼──────────────────────────────
   1 │  missing       0.3       0.2

julia> @chain df begin
         @slice_min(b, n = 3)
       end
3×3 DataFrame
 Row │ a          b         c         
     │ Float64?   Float64?  Float64?  
─────┼────────────────────────────────
   1 │ missing         0.3        0.2
   2 │ missing         0.3  missing   
   3 │       0.2       2.0        0.2  
   
julia> @chain df begin
         @slice_min(b, prop = 0.5, missing_rm = true)
       end
3×3 DataFrame
 Row │ a          b         c         
     │ Float64?   Float64?  Float64?  
─────┼────────────────────────────────
   1 │ missing         0.3        0.2
   2 │ missing         0.3  missing   
   3 │       0.2       2.0        0.2
```
