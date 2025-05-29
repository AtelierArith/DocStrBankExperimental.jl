```
update_pdf_font(;
    target::AbstractString = "tessdata",
    frequency::Integer = 7,
    source::GitHubProject = PDF_FONT_REPO
)::Bool
```

Update the PDF font file.  This is only needed when generating PDF files.  Returns false if there was an error updating the files.

**Arguments:**

| T   | Name      | Default    | Description                                           |
|:--- |:--------- |:---------- |:----------------------------------------------------- |
| K   | target    | `tessdata` | The directory to save the font file in.               |
| K   | frequency | `7`        | How often to check for updates on the server in days. |
| K   | source    | ...        | The GitHub project to download the font file from.    |

**Details:**

By default the data files are saved in a "tessdata" directory under the current directory. The training data is normally downloaded from the https://github.com/tesseract-ocr/tessdata_best GitHub project.

See also: [`download_pdf_font`](@ref)
