```
get_highlights_comments_pages(
    target::String;
    concatenate::Bool=true
) -> Tuple{Vector{String}, Vector{String}, Vector{Int32}}
```

Extract the highlights, comments, and pages from a passed PDF or all PDFs found recursively in the passed directory.

# Arguments

  * `target::String`: a PDF file or a directory with PDF files

# Keywords

  * `concatenate::Bool=true`: if `true`, concatenate the highlights

# Returns

  * `Tuple{Vector{String}, Vector{String}, Vector{Int32}}`: the highlights, comments, and pages

# Throws

  * [`DoesNotExist`](@ref): the specified file or directory doesn't exist
  * [`NotPDF`](@ref): the specified path does not end in `.pdf`

# Example

```jldoctest; output = false
using PDFHighlights

path_to_pdf_dir = joinpath(pathof(PDFHighlights) |> dirname |> dirname, "test", "pdf")
path_to_pdf = joinpath(path_to_pdf_dir, "TestPDF.pdf")

get_highlights_comments_pages(path_to_pdf_dir) ==
get_highlights_comments_pages(path_to_pdf) ==
(
    [
        "Highlight 1",
        "Highlight 2 Highlight 3",
        "Highlight 4",
        "Highhighlight 5",
        "6th Highhigh light-",
        "High light 7",
        "8th Highlight-",
    ],
    ["Comment 1", "Comment 2 Comment 3", "Comment 4", "", "", "", ""],
    Int32[1, 2, 4, 6, 7, 8, 9],
)

# output

true
```
