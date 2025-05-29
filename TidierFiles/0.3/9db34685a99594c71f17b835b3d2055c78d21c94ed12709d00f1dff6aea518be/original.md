```
write_dta(df, path)
```

Write a DataFrame to a Stata (.dta) file.

# Arguments

  * `df`: The DataFrame to be written to a file.
  * `path`: String as path where the .dta file will be created. If a file at this path already exists, it will be overwritten.

# Examples

```jldoctest
julia> df = DataFrame(AA=["sav", "por"], AB=[10.1, 10.2]);

julia> write_dta(df, "test.dta")
2×2 ReadStatTable:
 Row │     AA        AB 
     │ String  Float64? 
─────┼──────────────────
   1 │    sav      10.1
   2 │    por      10.2
```
