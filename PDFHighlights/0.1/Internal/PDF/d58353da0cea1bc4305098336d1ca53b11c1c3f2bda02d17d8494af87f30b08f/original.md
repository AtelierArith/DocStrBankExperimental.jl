```
get_author_title(pdf::String) -> Tuple{String, String}
```

Extract the author and title from the PDF.

# Arguments

  * `pdf::String`: absolute or relative path to the PDF file

# Returns

  * `Tuple{String, String}`: the author and title

# Throws

  * [`FileDoesNotExist`](@ref): the specified file doesn't exist
  * [`NotPDF`](@ref): the specified path does not end in `.pdf`

# Example

```jldoctest; output = false
using PDFHighlights

path_to_pdf = joinpath(
    pathof(PDFHighlights) |> dirname |> dirname,
    "test",
    "pdf",
    "TestPDF.pdf",
)

get_author_title(path_to_pdf) == ("Pavel Sobolev", "A dummy PDF for tests")

# output

true
```
