```
@drop_missing(df, [cols...])
```

Drop all rows with missing values.

When called without arguments, `@drop_missing()` drops all rows with missing values in any column. If columns are provided as an optional argument, only missing values from named columns are considered when dropping rows.

# Arguments

  * `df`: A DataFrame or GroupedDataFrame.
  * `cols...`: An optional column, or multiple columns separated by commas or specified using selection helpers.

# Examples

```jldoctest
julia> df = DataFrame(
              a = [1, 2, missing, 4],
              b = [1, missing, 3, 4]
            )
4×2 DataFrame
 Row │ a        b       
     │ Int64?   Int64?  
─────┼──────────────────
   1 │       1        1
   2 │       2  missing 
   3 │ missing        3
   4 │       4        4

julia> @chain df @drop_missing()
2×2 DataFrame
 Row │ a      b     
     │ Int64  Int64 
─────┼──────────────
   1 │     1      1
   2 │     4      4

julia> @chain df @drop_missing(a)
3×2 DataFrame
 Row │ a      b       
     │ Int64  Int64?  
─────┼────────────────
   1 │     1        1
   2 │     2  missing 
   3 │     4        4

julia> @chain df @drop_missing(a, b)
2×2 DataFrame
 Row │ a      b     
     │ Int64  Int64 
─────┼──────────────
   1 │     1      1
   2 │     4      4

julia> @chain df @drop_missing(starts_with("a"))
3×2 DataFrame
 Row │ a      b       
     │ Int64  Int64?  
─────┼────────────────
   1 │     1        1
   2 │     2  missing 
   3 │     4        4
```
