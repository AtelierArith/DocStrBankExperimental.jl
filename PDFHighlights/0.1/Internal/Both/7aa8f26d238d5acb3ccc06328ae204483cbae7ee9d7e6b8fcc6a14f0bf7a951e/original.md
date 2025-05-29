```
get_titles(target::String) -> Vector{String}
```

Get values from the `Titles` column if a CSV file is passed, or get the titles of all PDFs found recursively if a directory is passed.

# Arguments

  * `target::String`: a CSV file or a directory with PDF files

# Returns

  * `Vector{String}`: the titles

# Throws

  * [`NotCSVorDir`](@ref): the specified path does not end in `.csv` and is not a directory
  * Exceptions from: [`_get_titles_from_CSV`](@ref), [`_get_titles_from_PDF`](@ref)

# Example

```jldoctest; output = false
using PDFHighlights
HEADER = PDFHighlights.Internal.Constants.HEADER

path_to_pdf_dir = joinpath(pathof(PDFHighlights) |> dirname |> dirname, "test", "pdf")

(get_titles(path_to_pdf_dir) == ["A dummy PDF for tests"]) |> println

_file, io = mktemp()
println(io, HEADER, '\n', ",\"Girl, Interrupted\",,,1")
flush(io)
file = _file * ".csv"
mv(_file, file)

get_titles(file) == ["Girl, Interrupted"]

# output

true
true
```
