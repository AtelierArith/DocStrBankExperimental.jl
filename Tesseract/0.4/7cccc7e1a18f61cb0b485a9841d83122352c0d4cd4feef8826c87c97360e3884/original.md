```
tess_pipeline_word_box(
    func::Function,
    pipe::TessPipeline
)::Bool
```

Generate a BOX file from the pipeline and pass it back to the client via a callback. Returns `false` if there is a problem adding the BOX generator to the output.

**Arguments:**

| T   | Name | Default | Description                                  |
|:--- |:---- |:------- |:-------------------------------------------- |
| R   | func |         | The function to call with the lines of text. |
| R   | pipe |         | The pipline to collect the BOX data from.    |

**Details:**

The text will be passed to the caller one line at a time. The "\n" line terminator will be included with the text.

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

count = 0
tess_pipeline_word_box(pipeline) do line
    global count
    if count < 10
        print(line)
    end
    count += 1
end

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
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
true
```

See also: [`tess_run_pipeline`](@ref), [`tess_pipeline_unlv`](@ref),           [`tess_pipeline_lstm_box`](@ref)
