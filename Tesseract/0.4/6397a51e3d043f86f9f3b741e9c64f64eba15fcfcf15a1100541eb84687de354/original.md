```
tess_pipeline_unlv(
    func::Function,
    pipe::TessPipeline
)::Bool
```

Generate an UNLV file from the pipeline and pass it back to the client via a callback. Returns `false` if there is a problem adding the UNLV generator to the output.

**Arguments:**

| T   | Name | Default | Description                                  |
|:--- |:---- |:------- |:-------------------------------------------- |
| R   | func |         | The function to call with the lines of text. |
| R   | pipe |         | The pipline to collect the text from.        |

**Details:**

The text will be passed to the caller one line at a time. The "\n" line terminator will be included with the text.  Tesseract generates UNLV text in Latin-1, this method will transcode it to UTF-8 to work with Julia.

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

count = 0
tess_pipeline_unlv(pipeline) do line
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
true
```

See also: [`tess_run_pipeline`](@ref), [`tess_pipeline_word_box`](@ref),           [`tess_pipeline_lstm_box`](@ref), [`tess_pipeline_unlv_latin1`](@ref)
