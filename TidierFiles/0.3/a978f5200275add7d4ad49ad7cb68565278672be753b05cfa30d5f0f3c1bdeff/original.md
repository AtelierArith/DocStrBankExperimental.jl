```
function read_sas(data_file;  encoding=nothing, col_select=nothing, skip=0, n_max=Inf, num_threads)
```

Read data from a SAS (.sas7bdat and .xpt) file into a DataFrame, supporting both local and remote sources.

# Arguments

  * `filepath`: The path to the .dta file or a URL pointing to such a file. If a URL is provided, the file will be downloaded and then read.

`encoding`: Optional; specifies the encoding of the input file. If not provided, defaults to the package's or function's default. `col_select`: Optional; allows specifying a subset of columns to read. This can be a vector of column names or indices. If nothing, all columns are read.

  * `skip=0`: Number of rows at the beginning of the file to skip before reading.
  * `n_max=Inf`: Maximum number of rows to read from the file, after skipping. If Inf, read all available rows.

`num_threads`: specifies the number of concurrent tasks or threads to use for processing, allowing for parallel execution. Defaults to 1

# Examples

```jldoctest
julia> df = DataFrame(AA=["sav", "por"], AB=[10.1, 10.2]);

julia> write_sas(df, "test.sas7bdat");

julia> read_sas("test.sas7bdat")
2×2 DataFrame
 Row │ AA       AB      
     │ String3  Float64 
─────┼──────────────────
   1 │ sav         10.1
   2 │ por         10.2

julia> write_sas(df, "test.xpt");

julia> read_sas("test.xpt")
2×2 DataFrame
 Row │ AA       AB      
     │ String3  Float64 
─────┼──────────────────
   1 │ sav         10.1
   2 │ por         10.2
```
