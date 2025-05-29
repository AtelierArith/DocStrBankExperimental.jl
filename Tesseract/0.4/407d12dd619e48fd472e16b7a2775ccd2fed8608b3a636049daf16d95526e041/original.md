```
tess_run_pipeline(
    pipe::TessPipeline,
    filename::AbstractString;
    retryConfig::AbstractString = "",
    timeout::Integer = Int32(0)
)::Bool
```

Run the pipline against a file that contains the list of images to process or a TIFF file with multiple images.  Returns `false` if the process fails.

**Arguments:**

| T   | Name        | Default    | Description                                                   |
|:--- |:----------- |:---------- |:------------------------------------------------------------- |
| R   | pipe        |            | The pipline we're going to execute.                           |
| R   | filename    |            | The name of the file to read.                                 |
| K   | retryConfig | `""`       | A configuration file to load if an image cannot be processed. |
| K   | timeout     | `Int32(0)` | The maximum time in milliseconds to spend per page.           |

**Details:**

This method provides a simplified version of the `tess_run_pipeline` function.  This uses method exposed by the Tesseract library to process a list of files or a single TIFF file without additional input.

This method can only be used "once".  After it's called new output needs to be added to the pipeline if you want to reuse the [`TessPipeline`](@ref) object.

**Examples:**

Providing a file with a list of images to process:

```jldoctest
using Tesseract
using Suppressor

# Generate some pages to load.
write("page01.tiff", sample_tiff())
write("page02.tiff", sample_tiff())
write("page03.tiff", sample_tiff())

download_languages() # Make sure we have the data files.

instance = TessInst()
pipeline = TessPipeline(instance)

book = tess_pipeline_text(pipeline)

# Create a text file with the files to process.
open("pages.lst", create = true, write = true) do io
    println(io, "page01.tiff")
    println(io, "page02.tiff")
    println(io, "page03.tiff")
end

@suppress tess_run_pipeline(pipeline, "pages.lst")

for line in split(book[], "\n")[1:10]
    println(line)
end

# output

No one would have believed in the last years of the

the nineteenth century that this world was being watched
watched keenly and closely by intelligences greater than
than man’s and yet as mortal as his own; that as men busied
busied themselves about their various concerns they were
were scrutinised and studied, perhaps almost as narrowly as
as a man with a microscope might scrutinise the transient
transient creatures that swarm and multiply in a drop of
```

Using a multipage TIFF:

```jldoctest
using Tesseract
using Suppressor

# Generate some pages to load.
pix_write_tiff("book.tiff", sample_pix())
pix_write_tiff("book.tiff", sample_pix(); append = true)
pix_write_tiff("book.tiff", sample_pix(); append = true)

download_languages() # Make sure we have the data files.

instance = TessInst()
pipeline = TessPipeline(instance)

book = tess_pipeline_text(pipeline)

@suppress tess_run_pipeline(pipeline, "book.tiff")

for line in split(book[], "\n")[1:10]
    println(line)
end

# output

No one would have believed in the last years of the

the nineteenth century that this world was being watched
watched keenly and closely by intelligences greater than
than man’s and yet as mortal as his own; that as men busied
busied themselves about their various concerns they were
were scrutinised and studied, perhaps almost as narrowly as
as a man with a microscope might scrutinise the transient
transient creatures that swarm and multiply in a drop of
```

See also: [`TessPipeline`](@ref), [`tess_pipeline_text`](@ref)
