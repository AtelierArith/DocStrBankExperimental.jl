```
tess_alto(
    inst::TessInst,
    page::Integer = Int32(1)
)::Union{String, Nothing}
```

Extract the text in ALTO format from the image.  Returns `nothing` if there is an error.

**Arguments:**

| T   | Name | Default    | Description                            |
|:--- |:---- |:---------- |:-------------------------------------- |
| R   | inst |            | The instance to grab the text from.    |
| O   | page | `Int32(1)` | The page to extract the ALTO text for. |

**Details:**

This method will call `tess_recognize()` if it has not been called yet for the image.  The current ALTO spec can be accessed at https://github.com/altoxml/documentation/wiki/Versions.

**Example:**

```jldoctest
using Tesseract

download_languages()

instance = TessInst()
pix = sample_pix()

tess_image(instance, pix)
tess_resolution(instance, 72)

alto = tess_alto(instance)

for line in split(alto, '\n'; keepempty = false)[1:5]
    println(strip(line))
end

# output

<Page WIDTH="500" HEIGHT="600" PHYSICAL_IMG_NR="0" ID="page_0">
<PrintSpace HPOS="0" VPOS="0" WIDTH="500" HEIGHT="600">
<ComposedBlock ID="cblock_0" HPOS="10" VPOS="9" WIDTH="479" HEIGHT="514">
<TextBlock ID="block_0" HPOS="11" VPOS="9" WIDTH="406" HEIGHT="14">
<TextLine ID="line_0" HPOS="11" VPOS="9" WIDTH="406" HEIGHT="14">
```

See also: [`tess_text`](@ref), [`tess_hocr`](@ref), [`tess_tsv`](@ref), [`tess_parsed_tsv`](@ref), [`tess_confidences`](@ref)
