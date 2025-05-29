```
get_all(csv::String) -> Tuple{
    Vector{String},
    Vector{String},
    Vector{String},
    Vector{String},
    Vector{Int32},
}
```

Extract the values of all columns from the CSV file.

# Arguments

  * `csv::String`: absolute or relative path to the CSV file

# Returns

  * `Tuple{Vector{String}, Vector{String}, Vector{String}, Vector{String}, Vector{Int32}}`: the highlights, titles, authors, notes, and locations

# Throws

  * [`IntegrityCheckFailed`](@ref): another exception was thrown while checking the integrity of the table
  * Exceptions from: [`initialize`](@ref)

# Example

```jldoctest; output = false
using PDFHighlights
HEADER = PDFHighlights.Internal.Constants.HEADER

_file, io = mktemp()
row = string(
    "The world didn't stop spinning,",
    "\"Girl, Interrupted\",",
    "Susanna Kaysen,",
    "Journal,",
    "5722",
)
println(io, HEADER, '\n', row)
flush(io)
file = _file * ".csv"
mv(_file, file)

get_all(file) == (
    ["The world didn't stop spinning"],
    ["Girl, Interrupted"],
    ["Susanna Kaysen"],
    ["Journal"],
    [5722],
)

# output

true
```
