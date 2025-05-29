```
parse_columns_CSV(data_file, num_columns)
```

This parses numbers from CSV file that is read in with `CSV.File`. That is useful in case the CSV files has tables that contain both strings (e.g., station names) and numbers (lat/lon/height) and you are only interested in the numbers

# Example

This example assumes that the data starts at line 18, that the columns are separated by spaces, and that it contains at most 4 columns with data:

```julia-repl
julia> using CSV
julia> data_file        =   CSV.File("FileName.txt",datarow=18,header=false,delim=' ')
julia> data = parse_columns_CSV(data_file, 4)
```
