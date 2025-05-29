```
tess_pipeline_text(
    pipe::TessPipeline
)::Union{TessOutput{String}, Nothing}
```

Generate a text file from the pipeline and save it to a string.  Returns `nothing` if there is a problem adding the text generator to the output.

**Arguments:**

| T   | Name | Default | Description                           |
|:--- |:---- |:------- |:------------------------------------- |
| R   | pipe |         | The pipline to collect the text from. |

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

book = tess_pipeline_text(pipeline)

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
end

count = 0
for line in split(book[], "\n")[1:10]
    global count
    if count < 10
        println(line)
    end
    count += 1
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

See also: [`tess_run_pipeline`](@ref), [`tess_pipeline_alto`](@ref),           [`tess_pipeline_hocr`](@ref), [`tess_pipeline_pdf`](@ref)           [`tess_pipeline_tsv`](@ref)
