```
ods_readall(filename_or_stream; <keyword arguments>)
```

Return a dictionary of tables|dictionaries|dataframes indexed by position or name in the original OpenDocument Spreadsheet (.ods) file or stream.

# Arguments

  * `fileaname_or_stream`: file name or stream as `Vector{UInt8}`
  * `sheetsNames=[]`: the list of sheet names from which to import data.
  * `sheetsPos=[]`: the list of sheet positions (starting from 1) from which to import data.
  * `ranges=[]`: a list of pair of touples defining the ranges in each sheet from which to import data, in the format ((tlr,tlc),(brr,brc))
  * `innerType="Matrix"`: the type of the inner container returned. Either "Matrix", "Dict" or "DataFrame"

# Notes

  * sheetsNames and sheetsPos can not be given together
  * ranges is defined using integer positions for both rows and columns
  * individual dictionaries or dataframes are keyed by the values of the cells in the first row specified in the range, or first row if `range` is not given
  * innerType="Matrix", differently from innerType="Dict", preserves original column order, it is faster and require less memory
  * using innerType="DataFrame" also preserves original column order and try to auto-convert column types (working for Int64, Float64, String, in that order)

# Examples

```julia
julia> outDic  = ods_readall("spreadsheet.ods";sheetsPos=[1,3],ranges=[((1,1),(3,3)),((2,2),(6,4))], innerType="Dict")
Dict{Any,Any} with 2 entries:
  3 => Dict{Any,Any}(Pair{Any,Any}("c",Any[33.0,43.0,53.0,63.0]),Pair{Any,Any}("b",Any[32.0,42.0,52.0,62.0]),Pair{Any,Any}("d",Any[34.0,44.0,54.…
  1 => Dict{Any,Any}(Pair{Any,Any}("c",Any[23.0,33.0]),Pair{Any,Any}("b",Any[22.0,32.0]),Pair{Any,Any}("a",Any[21.0,31.0]))
julia> data = @pipe HTTP.get("https://github.com/sylvaticus/OdsIO.jl/raw/master/test/spreadsheet.ods").body |> ods_readall(_)
Dict{Any, Any} with 3 entries:
  "Sheet1" => Any["h1" "h2" "h3"; "a" "b" "c"; "aa" "bb" "cc"]
  "Sheet2" => Any["a" "b" "c"; 21 22 23; 31 32 33]
  "Sheet3" => Any[nothing nothing nothing nothing; nothing "b" "c" "d"; … ; nothing 52 53 54; nothing 62 63 64]
```
