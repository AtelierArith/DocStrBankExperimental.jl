```
tess_pipeline_lstm_box(
    func::Function,
    pipe::TessPipeline
)::Bool
```

Generate a LSTM BOX file from the pipeline and pass it back to the client via a callback. Returns `false` if there is a problem adding the LSTM BOX generator to the output.

**Arguments:**

| T   | Name | Default | Description                                    |
|:--- |:---- |:------- |:---------------------------------------------- |
| R   | func |         | The function to call with the lines of text.   |
| R   | pipe |         | The pipline to collect the LSTM BOX data from. |

**Details:**

The text will be passed to the caller one line at a time. The "\n" line terminator will be included with the text.

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
tess_pipeline_lstm_box(pipeline) do line
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
true
```

See also: [`tess_run_pipeline`](@ref), [`tess_pipeline_word_box`](@ref),           [`tess_pipeline_unlv`](@ref)
