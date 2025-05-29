```
tess_text_box(
    inst::TessInst,
    page::Integer = Int32(1)
)::Union{String, Nothing}
```

Retrieve the boxes for the identified characters on the page.  If there is an error 'nothing' is returned.

**Arguments:**

| T   | Name | Default    | Description                     |
|:--- |:---- |:---------- |:------------------------------- |
| R   | inst |            | The Tesseract instance to call. |
| O   | page | `Int32(1)` | The page to get the data for.   |

**Details:**

This method will call `tess_recognize()` if it has not been called yet for the image.  The results are primarly useful for training purposes.

Each line in the result is a character identified with 6 values:

  * The character that was recognized.
  * The left edge of the character measured in pixels from the left edge.
  * The bottom edge of the character measured in pixels from the bottom of the image.
  * The right edge of the character measured in pixels from the left edge.
  * The top edge of the character measured in pixels from the bottom of the image.
  * The page used in the recogniztion 0 based.

**Example:**

```jldoctest"
using Tesseract

download_languages()

instance = TessInst()
pix = sample_pix()

tess_image(instance, pix)
tess_resolution(instance, 72)

box = tess_text_box(instance)

for line in split(box, '\n'; keepempty = false)[1:5]
  println(line)
end

# output

N 11 580 17 591 0
o 19 580 25 588 0
o 35 580 41 588 0
n 43 580 49 588 0
e 51 580 57 588 0
```

See also: [`tess_unlv`](@ref), [`tess_lstm_box`](@ref), [`tess_word_box`](@ref)
