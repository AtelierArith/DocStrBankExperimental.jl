```
tess_tsv(
    inst::TessInst,
    page::Integer = Int32(1)
)::Union{String, Nothing}
```

Retrieve the TSV results from an recognition as a string with tabbed separated values.

**Arguments:**

| T   | Name | Default    | Description                     |
|:--- |:---- |:---------- |:------------------------------- |
| R   | inst |            | The Tesseract instance to call. |
| O   | page | `Int32(1)` | The page to get the data for.   |

**Details:**

This method will call `tess_recognize()` if it has not been called yet for the image.

If you want to read the data take a look at `tess_parsed_tsv()` which parses it into a form that is easier to use.  If you just want to display the data to the user or write it to a file then this method will probably be fine.

This call basically returns the results of the recognition process.  Each line in the string identifies an "object" found by Tesseract.  The 12 values per line are as follows:

  * level - Identifies what the line describes.
  * page - This is the page number passed into the `tess_tsv()` method.
  * block - Identifies the block on the page.
  * paragraph - The paragraph number in the block.
  * line - The line in the paragraph.
  * word - The word in the line.
  * left - Left edge of the item in pixels.
  * top - Top edge of the item in pixels.
  * width - Width of the item in pixels.
  * height - Height of the item in pixels.
  * conf - How confident the OCR engine is of the word (`0` - `100`). `-1` if level is not 5.
  * text - The word that was decoded from the image.

Level identifies what information the line is providing:

  * `1` - Page information, added at the start of the page.
  * `2` - Block information, added at the start of a block.
  * `3` - Paragraph information, added at the start of a paragraph.
  * `4` - Line information, added at the start of a line.
  * `5` - Word information, identifies a word that was read from the page.

The left, top, width, and height values define a box in pixels that encompases the item.  So if the level is 1, the box describes the whole image.  If the level is `1`, then the box encloses the block that was extracted, and so on down to the word that was extracted.

**Example:**

```jldoctest; filter = r"(\s+)"
using Tesseract

download_languages()

instance = TessInst()
pix = sample_pix()

tess_image(instance, pix)
tess_resolution(instance, 72)

tsv = tess_tsv(instance)

for line in split(tsv, '\n'; keepempty = false)[2:6]
    println(strip(line))
end

# output

2	1	1	0	0	0	10	9	479	514	-1
3	1	1	1	0	0	11	9	406	14	-1
4	1	1	1	1	0	11	9	406	14	-1
5	1	1	1	1	1	11	9	14	11	95.791931	No
5	1	1	1	1	2	35	12	22	8	95.791931	one
```

See also: [`tess_tsv`](@ref), [`tess_hocr`](@ref), [`tess_alto`](@ref), [`tess_parsed_tsv`](@ref), [`tess_confidences`](@ref)
