```
tess_pipeline_unlv(
    pipe::TessPipeline
)::Union{TessOutput{String}, Nothing}
```

Generate an UNLV file from the pipeline and save it to a string.  Returns `nothing` if there is a problem adding the UNLV generator to the output.

**Arguments:**

| T   | Name | Default | Description                                |
|:--- |:---- |:------- |:------------------------------------------ |
| R   | pipe |         | The pipline to collect the UNLV text from. |

**Details:**

The Tesseract generates Latin-1 text however this function will transcode it to UTF-8 to interact with Julia correctly.

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

book = tess_pipeline_unlv(pipeline)

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
end

for line in split(book[], "\n")[1:10]
    println(line)
end

# output

No one would have believed in the last years of the
the nineteenth century that this world was being watched
watched keenly and closely by intelligences greater than
than man's and yet as mortal as his own; that as men busied
busied themselves about their various concerns they were
were scrutinised and studied, perhaps almost as narrowly as
as a man with a microscope might scrutinise the transient
transient creatures that swarm and multiply in a drop of
of water. With infinite complacency men went to and fro over
over this globe about their little affairs, serene in their
```

See also: [`tess_run_pipeline`](@ref), [`tess_pipeline_word_box`](@ref),           [`tess_pipeline_lstm_box`](@ref), [`tess_pipeline_unlv_latin1`](@ref)
