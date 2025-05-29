```
tess_word_box(
    inst::TessInst,
    page::Integer = Int32(1)
)::Union{String, Nothing}
```

Create a UTF8 box file with WordStr strings,  If there is an error 'nothing' is returned.

**Arguments:**

| T   | Name | Default    | Description                     |
|:--- |:---- |:---------- |:------------------------------- |
| R   | inst |            | The Tesseract instance to call. |
| O   | page | `Int32(1)` | The page to get the data for.   |

**Details:**

This method will call `tess_recognize()` if it has not been called yet for the image.  The results are probably used for training.

**Example:**

```jldoctest; filter = r"(\s+)"
using Tesseract

download_languages()

instance = TessInst()
pix = sample_pix()

tess_image(instance, pix)
tess_resolution(instance, 72)

box = tess_word_box(instance)

for line in split(box, '\n'; keepempty = false)[1:5]
    println(line)
end

# output

WordStr 11 577 417 591 0 #No one would have believed in the last years of the
    418 577 422 591 0
WordStr 11 557 457 571 0 #the nineteenth century that this world was being watched
    458 557 462 571 0
WordStr 10 537 457 551 0 #watched keenly and closely by intelligences greater than
```

See also: [`tess_unlv`](@ref), [`tess_lstm_box`](@ref), [`tess_text_box`](@ref)
