```
get_locations(csv::String) -> Vector{Int32}
```

Extract the values of the `Location` column from the CSV file.

# Arguments

  * `csv::String`: absolute or relative path to the CSV file

# Returns

  * `Vector{Int32}`: the locations

# Throws

  * Exceptions from: [`get_all`](@ref)

# Example

```jldoctest; output = false
using PDFHighlights
HEADER = PDFHighlights.Internal.Constants.HEADER

_file, io = mktemp()
println(io, HEADER, '\n', ",,,,5722")
flush(io)
file = _file * ".csv"
mv(_file, file)

get_locations(file) == Int32[5722]

# output

true
```
