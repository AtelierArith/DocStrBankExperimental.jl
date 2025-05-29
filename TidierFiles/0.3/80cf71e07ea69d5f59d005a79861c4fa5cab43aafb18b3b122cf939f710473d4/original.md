```
write_xlsx(x; path, overwrite)
```

Write a DataFrame, or multiple DataFrames, to an Excel file. Specific sheets on can be specified for each dataframe.

# Arguments

  * `x`: The data to write. Can be a single Pair{String, DataFrame} for writing one sheet, or a Tuple of such pairs for writing multiple sheets. The String in each pair specifies the sheet name, and the DataFrame is the data to write to that sheet.
  * `path`: The path to the Excel file where the data will be written.
  * `overwrite`: Defaults to false. Whether to overwrite an existing file. If false, an error is thrown when attempting to write to an existing file.

# Examples

```jldoctest
julia> df = DataFrame(integers=[1, 2, 3, 4],
       strings=["This", "Package makes", "File reading/writing", "even smoother"],
       floats=[10.2, 20.3, 30.4, 40.5]);

julia> df2 = DataFrame(AA=["aa", "bb"], AB=[10.1, 10.2]);

julia> write_xlsx(("REPORT_A" => df, "REPORT_B" => df2); path="xlsxtest.xlsx", overwrite = true);
```
