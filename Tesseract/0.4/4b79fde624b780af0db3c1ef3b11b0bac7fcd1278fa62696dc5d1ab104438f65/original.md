```
tess_unlv_latin1(
    inst::TessInst
)::Union{String, Nothing}
```

Extract the text in UNLV format Latin-1 with reject and suspect codes.  If there is an error `nothing` is returned.

**Arguments:**

| T   | Name | Default | Description                     |
|:--- |:---- |:------- |:------------------------------- |
| R   | inst |         | The Tesseract instance to call. |

**Details:**

This method will call `tess_recognize()` if it has not been called yet for the image.

This method is more used to test the OCR results than anything else.  This method returns the OCR data in Latin1 encoding.  If you want to use it as a string in Julia use the [`tess_unlv`](@ref) method which will convert it to UTF-8 for you.

**Example:**

```jldoctest
using Tesseract

download_languages()

instance = TessInst()
pix = sample_pix()

tess_image(instance, pix)
tess_resolution(instance, 72)

unlv = tess_unlv_latin1(instance)

# output

1470-element Vector{UInt8}:
 0x4e
 0x6f
 0x20
 0x6f
 0x6e
 0x65
 0x20
 0x77
 0x6f
 0x75
    ⋮
 0x6f
 0x6e
 0x6d
 0x65
 0x6e
 0x74
 0x2e
 0x0a
 0x0a
```

See also: [`tess_lstm_box`](@ref), [`tess_word_box`](@ref), [`tess_text_box`](@ref),           [`tess_unlv`](@ref)
