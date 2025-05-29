```
tess_run_pipeline(
    func::Function,
    pipe::TessPipeline,
    title::AbstractString = ""
)::Bool
```

Run the pipeline against a series of images.

**Arguments:**

| T   | Name  | Default | Description                          |
|:--- |:----- |:------- |:------------------------------------ |
| R   | func  |         | The callback to call for the images. |
| R   | pipe  |         | The pipline we're going to execute.  |
| O   | title | `""`    | Optional title for the document.     |

**Details:**

This is the primary function of the `TessPipeline` object.  This method is used to combine output from multiple images into a single document (or multiple documents of different types).

The argument passed back to the function is a method with the form:

```
function add(Pix, Integer)::Bool
```

The client calls this method with the image and pixels per inch of the image.  The image will be processed immediately and added to the pipeline's output.

If you the callback returns false then the `tess_run_pipeline()` will return `false`.  If it doesn't return a boolean or returns `true` then `tess_run_pipeline()` returns `true` assuming there are no other errors.

This method can only be used "once".  After it's called new output needs to be added to the pipeline if you want to reuse the [`TessPipeline`](@ref) object.

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
