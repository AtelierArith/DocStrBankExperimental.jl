```
tess_pipeline_word_box(
    pipe::TessPipeline,
    filename::AbstractString
)::Bool
```

Generate a BOX file from the pipeline and save it to the specified file.  Returns `false` if there is a problem adding the BOX generator to the output.

**Arguments:**

| T   | Name     | Default | Description                          |
|:--- |:-------- |:------- |:------------------------------------ |
| R   | pipe     |         | The pipline to collect the BOX from. |
| R   | filename |         | The file to write the BOX to.        |

**Details:**

If the file exists it will be overwritten.

**Examples:**

```jldoctest; filter = r"(\s+)"
using Tesseract

# Generate some pages to load.
write("page01.tiff", sample_tiff())
write("page02.tiff", sample_tiff())
write("page03.tiff", sample_tiff())

download_languages() # Make sure we have the data files.

instance = TessInst()
pipeline = TessPipeline(instance)

tess_pipeline_word_box(pipeline, "My Book.box")

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
end

for line in readlines("My Book.box")[1:10]
    println(line)
end

# output

WordStr 11 577 417 591 0 #No one would have believed in the last years of the
   418 577 422 591 0
WordStr 11 557 457 571 0 #the nineteenth century that this world was being watched
   458 557 462 571 0
WordStr 10 537 457 551 0 #watched keenly and closely by intelligences greater than
   458 537 462 551 0
WordStr 11 517 481 531 0 #than man’s and yet as mortal as his own; that as men busied
   482 517 486 531 0
WordStr 11 497 457 511 0 #busied themselves about their various concerns they were
   458 497 462 511 0
```

See also: [`tess_run_pipeline`](@ref), [`tess_pipeline_unlv`](@ref),           [`tess_pipeline_lstm_box`](@ref)
