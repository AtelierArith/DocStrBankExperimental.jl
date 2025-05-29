```
tess_pipeline_unlv_latin1(
    pipe::TessPipeline
)::Union{TessOutput{Vector{UInt8}}, Nothing}
```

Generate an UNLV file from the pipeline and save it to a byte array.  Returns `nothing` if there is a problem adding the UNLV generator to the output.

**Arguments:**

| T   | Name | Default | Description                                |
|:--- |:---- |:------- |:------------------------------------------ |
| R   | pipe |         | The pipline to collect the UNLV text from. |

**Details:**

The returned bytes will be in Latin-1 encoding, so a conversion would be required before using the bytes as a string in Julia.  [`tess_pipeline_unlv`](@ref) will provide you with the same data but already encoded in UTF-8 for Julia.

**Examples:**

```jldoctest
using Tesseract

# Generate some pages to load.
write("page01.tiff", sample_tiff())
write("page02.tiff", sample_tiff())
write("page03.tiff", sample_tiff())

download_languages() # Make sure we have the data files.

instance = TessInst()
pipeline = TessPipeline(instance)

bytes = tess_pipeline_unlv_latin1(pipeline)

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
end

println(string("Book generated: ", length(bytes[]), " bytes."))

# output

Book generated: 4410 bytes.
```

See also: [`tess_run_pipeline`](@ref), [`tess_pipeline_word_box`](@ref),           [`tess_pipeline_lstm_box`](@ref), [`tess_pipeline_unlv`](@ref)
