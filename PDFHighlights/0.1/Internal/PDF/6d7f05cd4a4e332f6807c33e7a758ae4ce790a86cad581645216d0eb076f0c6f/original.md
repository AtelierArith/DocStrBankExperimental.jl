```
get_authors_titles(dir::String) -> Tuple{Vector{String}, Vector{String}}
```

Extract the authors and titles from all PDFs found recursively in the passed directory.

# Arguments

  * `dir::String`: a directory with PDF files

# Returns

  * `Tuple{Vector{String}, Vector{String}}`: the authors and titles

# Throws

  * [`DirectoryDoesNotExist`](@ref): the specified directory doesn't exist
  * Exceptions from: [`get_author_title`](@ref)

# Example

```jldoctest; output = false
using PDFHighlights

path_to_pdf_dir = joinpath(pathof(PDFHighlights) |> dirname |> dirname, "test", "pdf")

get_authors_titles(path_to_pdf_dir) == (["Pavel Sobolev"], ["A dummy PDF for tests"])

# output

true
```
