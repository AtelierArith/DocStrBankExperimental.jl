```
tess_pipeline_alto(
    func::Function,
    pipe::TessPipeline
)::Bool
```

Generate an ALTO file from the pipeline and pass it back to the client via a callback. Returns `false` if there is a problem adding the ALTO generator to the output.

**Arguments:**

| T   | Name | Default | Description                                  |
|:--- |:---- |:------- |:-------------------------------------------- |
| R   | func |         | The function to call with the lines of text. |
| R   | pipe |         | The pipline to collect the text from.        |

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
tess_pipeline_alto(pipeline) do line
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

<?xml version="1.0" encoding="UTF-8"?>
<alto xmlns="http://www.loc.gov/standards/alto/ns-v3#" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.loc.gov/standards/alto/ns-v3# http://www.loc.gov/alto/v3/alto-3-0.xsd">
    <Description>
        <MeasurementUnit>pixel</MeasurementUnit>
        <sourceImageInformation>
            <fileName>My First Book</fileName>
        </sourceImageInformation>
        <OCRProcessing ID="OCR_0">
            <ocrProcessingStep>
                <processingSoftware>
true
```

See also: [`tess_run_pipeline`](@ref), [`tess_pipeline_hocr`](@ref),           [`tess_pipeline_pdf`](@ref), [`tess_pipeline_text`](@ref)           [`tess_pipeline_tsv`](@ref)
