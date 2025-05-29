```
tess_pipeline_pdf(
    pipe::TessPipeline,
    filename::AbstractString;
    textOnly::Bool = false,
    dataDir::AbstractString = TESS_DATA
)::Bool
```

Generate a PDF file from the pipeline and save it to the specified file.  Returns `false` if there is a problem adding the PDF generator to the output.

**Arguments:**

| T   | Name     | Default | Description                                                  |
|:--- |:-------- |:------- |:------------------------------------------------------------ |
| R   | pipe     |         | The pipline to collect the tsv from.                         |
| R   | filename |         | The file to write the tsv to.                                |
| K   | textOnly |         | Should the PDF just include text or also contain the images? |
| K   | dataDir  |         | The directory to look for the PDF font file in.              |

**Details:**

If the file exists it will be overwritten.  A text only PDF will appear empty since Tesseract uses a glyphless font, however you will be able to search for the text and see and "empty" page where it's found.  Normally textOnly is false and will include the image scanned by Tesseract which gives you a searchable PDF with the images.

**Examples:**

```jldoctest
using Tesseract

# Generate some pages to load.
write("page01.tiff", sample_tiff())
write("page02.tiff", sample_tiff())
write("page03.tiff", sample_tiff())

download_languages() # Make sure we have the data files.
download_pdf_font() # Make sure we have the PDF font file.

instance = TessInst()
pipeline = TessPipeline(instance)

tess_pipeline_pdf(pipeline, "My Book.pdf")

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
end

println(string("PDF created: ", filesize("My Book.pdf"), " bytes."))

# output

PDF created: 316722 bytes.
```

See also: [`tess_run_pipeline`](@ref), [`tess_pipeline_alto`](@ref),           [`tess_pipeline_hocr`](@ref), [`tess_pipeline_text`](@ref)           [`tess_pipeline_tsv`](@ref)
