```
read_arrow(df, path)
```

Read an Arrow file (.arrow) to a DataFrame.

# Arguments

  * `df`: The DataFrame to be written to a file.
  * `path`: String as path where the .dta file will be created. If a file at this path already exists, it will be overwritten.
  * `skip`: Number of initial lines to skip before reading data. Default is 0.
  * `n_max`: Maximum number of rows to read. Default is Inf (read all rows).
  * `col_select`: Optional vector of symbols or strings to select which columns to load.

# Examples

```jldoctest
julia> df = DataFrame(AA=["Arr", "ow"], AB=[10.1, 10.2]);

julia> write_arrow(df , "test.arrow");

julia> read_arrow("test.arrow")
2×2 DataFrame
 Row │ AA      AB      
     │ String  Float64 
─────┼─────────────────
   1 │ Arr        10.1
   2 │ ow         10.2
```
