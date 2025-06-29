```
get_title(pdf::String) -> String
```

Extract the title from the PDF.

# Arguments

  * `pdf::String`: absolute or relative path to the PDF file

# Returns

  * `String`: the title

# Throws

  * Exceptions from: [`get_author_title`](@ref)

# Example

```jldoctest; output = false
using PDFHighlights

path_to_pdf = joinpath(
    pathof(PDFHighlights) |> dirname |> dirname,
    "test",
    "pdf",
    "TestPDF.pdf",
)

get_title(path_to_pdf) == "A dummy PDF for tests"

# output

true
```
