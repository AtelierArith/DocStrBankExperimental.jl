```
read_xlsx(path; sheet, range, col_names, col_types, missing_value, trim_ws, skip, n_max, guess_max)
```

Read data from an Excel file into a DataFrame.

# Arguments

  * `path`: The path to the Excel file to be read.
  * `sheet`: Specifies the sheet to be read. Can be either the name of the sheet as a string or its index as an integer. If nothing, the first sheet is read.
  * `range`: Specifies a specific range of cells to be read from the sheet. If nothing, the entire sheet is read.
  * `col_names`: Indicates whether the first row of the specified range should be treated as column names. If false, columns will be named automatically.
  * `col_types`: Allows specifying column types explicitly. Can be a single type applied to all columns, a list or a dictionary mapping column names or indices to types. If nothing, types will be inferred.
  * `missing_value`: The value or vector that represents missing values in the Excel file. Unlike CSV.jl based functions, everything does not need to be written as a string
  * `trim_ws`: Whether to trim leading and trailing whitespace from cells in the Excel file.
  * `skip`: Number of rows to skip at the beginning of the sheet or range before reading data.
  * `n_max`: The maximum number of rows to read from the sheet or range, after skipping. Inf means read all available rows.
  * `guess_max`: The maximum number of rows to scan for type guessing and column names detection. Only relevant if col*types is nothing or col*names is true. If nothing, a default heuristic is used.

# Examples

```jldoctest
julia> df = DataFrame(integers=[1, 2, 3, 4],
       strings=["This", "Package makes", "File reading/writing", "even smoother"],
       floats=[10.2, 20.3, 30.4, 40.5]);

julia> df2 = DataFrame(AA=["aa", "bb"], AB=[10.1, 10.2]);

julia> write_xlsx(("REPORT_A" => df, "REPORT_B" => df2); path="xlsxtest.xlsx", overwrite = true);

julia> read_xlsx("xlsxtest.xlsx", sheet = "REPORT_A", skip = 1, n_max = 4, missing_value = [2])
3×3 DataFrame
 Row │ integers  strings               floats   
     │ Int64?    String?               Float64? 
─────┼──────────────────────────────────────────
   1 │  missing  Package makes             20.3
   2 │        3  File reading/writing      30.4
   3 │        4  even smoother             40.5
```
