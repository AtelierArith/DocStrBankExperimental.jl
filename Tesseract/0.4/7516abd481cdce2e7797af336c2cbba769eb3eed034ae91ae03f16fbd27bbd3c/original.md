```
tess_hocr(
    inst::TessInst,
    page::Integer = Int32(1)
)::Union{String, Nothing}
```

Extract the text in hOCR format from the image.  Returns `nothing` if there is an error.

**Arguments:**

| T   | Name | Default    | Description                            |
|:--- |:---- |:---------- |:-------------------------------------- |
| R   | inst |            | The instance to grab the text from.    |
| O   | page | `Int32(1)` | The page to extract the hOCR text for. |

**Details:**

This method will call `tess_recognize()` if it has not been called yet for the image.  The current hOCR spec can be accessed at http://kba.cloud/hocr-spec/1.2/.

**Example:**

```jldoctest
using Tesseract

download_languages()

instance = TessInst()
pix = sample_pix()

tess_image(instance, pix)
tess_resolution(instance, 72)

hocr = tess_hocr(instance)

for line in split(hocr, '\n'; keepempty = false)[1:5]
    println(strip(line))
end

# output

<div class='ocr_page' id='page_1' title='image "unknown"; bbox 0 0 500 600; ppageno 0; scan_res 72 72'>
<div class='ocr_carea' id='block_1_1' title="bbox 10 9 489 523">
<p class='ocr_par' id='par_1_1' lang='eng' title="bbox 11 9 417 23">
<span class='ocr_line' id='line_1_1' title="bbox 11 9 417 23; baseline 0 -3; x_size 22.717392; x_descenders 5.5; x_ascenders 5.7391305">
<span class='ocrx_word' id='word_1_1' title='bbox 11 9 25 20; x_wconf 95'>No</span>
```

See also: [`tess_text`](@ref), [`tess_alto`](@ref), [`tess_tsv`](@ref),           [`tess_parsed_tsv`](@ref), [`tess_confidences`](@ref)
