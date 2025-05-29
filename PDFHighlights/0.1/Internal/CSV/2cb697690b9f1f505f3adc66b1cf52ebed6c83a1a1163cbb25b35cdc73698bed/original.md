```
import_highlights(csv::String, target::String; quiet::Bool=false) -> Nothing
```

Import the highlights (and related data) into a CSV file from a PDF file or directory with PDF files.

# Arguments

  * `csv::String`: absolute or relative path to the CSV file
  * `target::String`: a PDF file or a directory with PDF files

# Keywords

  * `quiet::Bool=false`: if `true`, don't print to standard output

# Throws

  * [`IntegrityCheckFailed`](@ref): another exception was thrown while checking the integrity of the table
  * Exceptions from: [`initialize`](@ref)

# Example

```jldoctest; output = false
using PDFHighlights
using Suppressor

path_to_pdf_dir = joinpath(pathof(PDFHighlights) |> dirname |> dirname, "test", "pdf")
path_to_pdf = joinpath(path_to_pdf_dir, "TestPDF.pdf")

_file, io = mktemp()
file = _file * ".csv"
mv(_file, file)

(@capture_out(import_highlights(file, path_to_pdf)) ==
"""

    CSV: "$(basename(file))"
    PDF: "TestPDF.pdf"
    Highlights (found / added): 7 / 7

""") |> println

(@capture_out(import_highlights(file, path_to_pdf_dir)) ==
"""

    CSV: "$(basename(file))"
    Directory: "pdf"
    Highlights (found / added): 7 / 0

""") |> println

@capture_out(import_highlights(file, path_to_pdf; quiet=true)) == ""

# output

true
true
true
```
