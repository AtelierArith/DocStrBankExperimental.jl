```
tess_pipeline_pdf(
    pipe::TessPipeline;
    textOnly::Bool = false,
    dataDir::AbstractString = TESS_DATA
)::Union{TessOutput, Nothing}
```

Generate a PDF file from the pipeline and save it to a byte array.  Returns `nothing` if there is a problem adding the PDF generator to the output.

**Arguments:**

| T   | Name     | Default | Description                                                  |
|:--- |:-------- |:------- |:------------------------------------------------------------ |
| R   | pipe     |         | The pipline to collect the TSV data from.                    |
| K   | textOnly |         | Should the PDF just include text or also contain the images? |
| K   | dataDir  |         | The directory to look for the PDF font file in.              |

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

book = tess_pipeline_pdf(pipeline)

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
end

println(string("PDF created: ", length(book[]), " bytes."))

# output

PDF created: 316722 bytes.
```

See also: [`tess_run_pipeline`](@ref), [`tess_pipeline_alto`](@ref),           [`tess_pipeline_hocr`](@ref), [`tess_pipeline_text`](@ref)           [`tess_pipeline_tsv`](@ref)
