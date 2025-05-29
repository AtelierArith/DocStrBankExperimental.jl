```
tess_pipeline_unlv(
    pipe::TessPipeline,
    filename::AbstractString,
    utf8::Bool = true
)::Bool
```

Generate a UNLV test file from the pipeline and save it to the specified file.  Returns `false` if there is a problem adding the UNLV generator to the output.

**Arguments:**

| T   | Name     | Default | Description                                |
|:--- |:-------- |:------- |:------------------------------------------ |
| R   | pipe     |         | The pipline to collect the UNLV text from. |
| R   | filename |         | The file to write the UNLV text to.        |
| O   | utf8     | `true`  | Should the output be transcoded to UTF-8?  |

**Details:**

If the file exists it will be overwritten.  The Tesseract library outputs a file in Latin-1 encoding (even through all other formats are UTF-8).  We can use Julia to convert the file into UTF-8 to match the other encodings if desired.

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

tess_pipeline_unlv(pipeline, "My Book.unlv")

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
end

for line in readlines("My Book.unlv")[1:10]
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
