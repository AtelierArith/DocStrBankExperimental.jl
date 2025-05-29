```
tess_pipeline_hocr(
    pipe::TessPipeline,
    filename::AbstractString,
    fontInfo::Bool = false
)::Bool
```

Generate a HOCR file from the pipeline and save it to the specified file.  Returns `false` if there is a problem adding the HOCR generator to the output.

**Arguments:**

| T   | Name     | Default | Description                                        |
|:--- |:-------- |:------- |:-------------------------------------------------- |
| R   | pipe     |         | The pipline to collect the HORC text from.         |
| R   | filename |         | The file to write the HORC text to.                |
| O   | fontInfo | `false` | Should font information be included in the output? |

**Details:**

If the file exists it will be overwritten.

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

tess_pipeline_hocr(pipeline, "My Book.hocr")

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
end

for line in readlines("My Book.hocr")[1:10]
    println(line)
end

# output

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
    <head>
        <title>My First Book</title>
        <meta http-equiv="Content-Type" content="text/html;charset=utf-8"/>
        <meta name='ocr-system' content='tesseract 5.1.0' />
        <meta name='ocr-capabilities' content='ocr_page ocr_carea ocr_par ocr_line ocrx_word ocrp_wconf'/>
    </head>
```

See also: [`tess_run_pipeline`](@ref), [`tess_pipeline_alto`](@ref),           [`tess_pipeline_pdf`](@ref), [`tess_pipeline_text`](@ref)           [`tess_pipeline_tsv`](@ref)
