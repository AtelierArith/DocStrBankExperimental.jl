```
read_parquet(path)
```

Read a Paquet File (.parquet) to a DataFrame.

# Arguments

  * `path`: Path or vector of paths or URLs to parquet file to be read
  * `col_names`: Indicates if the first row of the CSV is used as column names. Can be true, false, or an array of strings. Default is true.
  * `skip`: Number of initial lines to skip before reading data. Default is 0.
  * `n_max`: Maximum number of rows to read. Default is Inf (read all rows).
  * `col_select`: Optional vector of symbols or strings to select which columns to load.

# Examples

```jldoctest
julia> df = DataFrame(AA=["Par", "quet"], AB=[10.1, 10.2]);

julia> write_parquet(df, "test.parquet");

julia> read_parquet("test.parquet")
2×2 DataFrame
 Row │ AA      AB      
     │ String  Float64 
─────┼─────────────────
   1 │ Par        10.1
   2 │ quet       10.2
```
