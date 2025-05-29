```
tess_pipeline_lstm_box(
    pipe::TessPipeline,
    filename::AbstractString
)::Bool
```

Generate a LSTM BOX file from the pipeline and save it to the specified file.  Returns `false` if there is a problem adding the LSTM BOX generator to the output.

**Arguments:**

| T   | Name     | Default | Description                               |
|:--- |:-------- |:------- |:----------------------------------------- |
| R   | pipe     |         | The pipline to collect the LSTM BOX from. |
| R   | filename |         | The file to write the LSTM BOX to.        |

**Details:**

If the file exists it will be overwritten.

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

tess_pipeline_lstm_box(pipeline, "My Book.box")

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
    true
end

for line in readlines("My Book.box")[1:10]
    println(line)
end

# output

N 11 577 422 591 0
o 11 577 422 591 0
  11 577 422 591 0
o 11 577 422 591 0
n 11 577 422 591 0
e 11 577 422 591 0
  11 577 422 591 0
w 11 577 422 591 0
o 11 577 422 591 0
u 11 577 422 591 0
```

See also: [`tess_run_pipeline`](@ref), [`tess_pipeline_word_box`](@ref),           [`tess_pipeline_unlv`](@ref)
