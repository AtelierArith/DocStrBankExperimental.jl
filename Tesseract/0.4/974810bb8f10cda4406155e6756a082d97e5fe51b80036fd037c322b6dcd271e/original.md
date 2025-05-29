```
tess_unlv(
    inst::TessInst
)::Union{String, Nothing}
```

Extract the text in UNLV format UTF-8 with reject and suspect codes.  If there is an error `nothing` is returned.

**Arguments:**

| T   | Name | Default | Description                     |
|:--- |:---- |:------- |:------------------------------- |
| R   | inst |         | The Tesseract instance to call. |

**Details:**

This method will call `tess_recognize()` if it has not been called yet for the image.

This method is more used to test the OCR results than anything else.  If you want the original Latin1 encoding use [`tess_unlv_latin1`](@ref) method.

**Example:**

```jldoctest
using Tesseract

download_languages()

instance = TessInst()
pix = sample_pix()

tess_image(instance, pix)
tess_resolution(instance, 72)

unlv = tess_unlv(instance)

for line in split(unlv, '\n'; keepempty = false)[1:5]
    println(line)
end

# output

No one would have believed in the last years of the
the nineteenth century that this world was being watched
watched keenly and closely by intelligences greater than
than man's and yet as mortal as his own; that as men busied
busied themselves about their various concerns they were
```

See also: [`tess_lstm_box`](@ref), [`tess_word_box`](@ref), [`tess_text_box`](@ref),           [`tess_unlv_latin1`](@ref)
