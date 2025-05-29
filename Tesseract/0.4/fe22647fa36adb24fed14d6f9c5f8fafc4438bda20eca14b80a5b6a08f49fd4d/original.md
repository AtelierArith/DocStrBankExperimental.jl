```
download_pdf_font(;
    target::AbstractString = "tessdata"
    baseUrl::AbstractString = PDF_FONT_URL,
    force::Bool = false
)::Bool
```

Download the PDF font file.  Returns `false` if there is a problem downloading the files.

**Arguments:**

| T   | Name    | Default    | Description                                      |
|:--- |:------- |:---------- |:------------------------------------------------ |
| K   | target  | `tessdata` | The directory to save the PDF font to.           |
| K   | baseUrl | ...        | The base URL to download the file from.          |
| K   | force   | `false`    | Should the file be downloaded even it it exists? |

**Details:**

By default "pdf.ttf" is downloaded from https://github.com/tesseract-ocr/tessconfigs. The client can specify a different URL to download the file from.  This file is needed when asking Tesseract to generate a PDF.

Normally if the file has already been downloaded then it is not downloaded again.  However if `force` is true then the file is downloaded and the existing file is overwritten.

See also: [`update_pdf_font`](@ref)
