```
ods_read(filename_or_stream; <keyword arguments>)
```

Return a  table|dictionary|dataframe from a sheet (or range within a sheet) in a OpenDocument Spreadsheet (.ods) file or stream.

# Arguments

  * `fileaname_or_stream`: file name or stream as `Vector{UInt8}`
  * `sheetName=nothing`: the sheet name from which to import data.
  * `sheetPos=nothing`: the position of the sheet (starting from 1) from which to import data.
  * `range=nothing`: a pair of touples defining the range in the sheet from which to import data, in the format ((tlr,tlc),(brr,brc))
  * `retType="Matrix"`: the type of container returned. Either "Matrix", "Dict" or "DataFrame"

# Notes

  * sheetName and sheetPos can not be given together
  * if both sheetName and sheetPos are not specified data from the first sheet is returned
  * ranges is defined using integer positions for both rows and columns
  * the dictionary or dataframe is keyed by the values of the cells in the first row specified in the range, or first row if `range` is not given
  * retType="Matrix", differently from innerType="Dict", preserves original column order, it is faster and require less memory
  * using innerType="DataFrame" also preserves original column order and try to auto-convert column types (working for Int64, Float64, String, in that order)

# Examples

```julia
julia> df = ods_read("spreadsheet.ods";sheetName="Sheet2",retType="DataFrame")
3×3 DataFrames.DataFrame
│ Row │ x1   │ x2   │ x3   │
├─────┼──────┼──────┼──────┤
│ 1   │ "a"  │ "b"  │ "c"  │
│ 2   │ 21.0 │ 22.0 │ 23.0 │
│ 3   │ 31.0 │ 32.0 │ 33.0 │
julia> data = @pipe HTTP.get("https://github.com/sylvaticus/OdsIO.jl/raw/master/test/spreadsheet.ods").body |> ods_read(_)
3×3 Matrix{Any}:
 "h1"  "h2"  "h3"
 "a"   "b"   "c"
 "aa"  "bb"  "cc"
```
