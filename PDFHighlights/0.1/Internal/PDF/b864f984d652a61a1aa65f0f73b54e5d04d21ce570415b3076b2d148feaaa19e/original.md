```
get_pages(
    target::String;
    concatenate::Bool=false
) -> Vector{Int32}
```

Extract the pages from a passed PDF or all PDFs found recursively in the passed directory.

# Arguments

  * `target::String`: a PDF file or a directory with PDF files

# Keywords

  * `concatenate::Bool=false`: if `true`, concatenate the highlights

# Returns

  * `Vector{Int32}`: the pages

# Throws

  * Exceptions from: [`get_highlights_comments_pages`](@ref)

# Example

```jldoctest; output = false
using PDFHighlights

path_to_pdf_dir = joinpath(pathof(PDFHighlights) |> dirname |> dirname, "test", "pdf")
path_to_pdf = joinpath(path_to_pdf_dir, "TestPDF.pdf")

get_pages(path_to_pdf_dir) == get_pages(path_to_pdf) == Int32[1, 2, 3, 4, 5, 6, 7, 8, 9]

# output

true
```
