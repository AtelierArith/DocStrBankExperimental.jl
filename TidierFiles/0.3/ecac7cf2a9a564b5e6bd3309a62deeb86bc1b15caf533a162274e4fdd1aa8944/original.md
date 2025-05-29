```
write_sav(df, path)
```

Write a DataFrame to a SPSS (.sav or .por) file.

# Arguments

  * `df`: The DataFrame to be written to a file.
  * `path`: String as path where the .dta file will be created. If a file at this path already exists, it will be overwritten.

# Examples

```jldoctest
julia> df = DataFrame(AA=["sav", "por"], AB=[10.1, 10.2]);

julia> write_sav(df, "test.sav")
2×2 ReadStatTable:
 Row │     AA        AB 
     │ String  Float64? 
─────┼──────────────────
   1 │    sav      10.1
   2 │    por      10.2

julia> write_sav(df, "test.por")
2×2 ReadStatTable:
 Row │     AA        AB 
     │ String  Float64? 
─────┼──────────────────
   1 │    sav      10.1
   2 │    por      10.2
```
