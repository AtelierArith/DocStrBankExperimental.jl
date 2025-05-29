```
initialize(csv::String) -> Nothing
```

If the file along the `csv` path does not exist, then create it and write the header; if it exists but is empty, do the same; if it exists and is not empty, check structural correctness.

# Arguments

  * `csv::String`: absolute or relative path to the CSV file

# Throws

  * [`NotCSV`](@ref): the specified path does not end in `.csv`
  * Exceptions from: [`_check`](@ref)

# Example

```jldoctest; output = false
using PDFHighlights
HEADER = PDFHighlights.Internal.Constants.HEADER

_file, _ = mktemp()
file = _file * ".csv"
mv(_file, file)

initialize(file)

open(file, "r") do io
    readlines(io) == [HEADER]
end

# output

true
```
