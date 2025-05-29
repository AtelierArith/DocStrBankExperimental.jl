```
tess_image(
        inst::TessInst,
        pix::Pix
    )::Nothing
```

Set the image to be OCRed.

**Arguments:**

| T   | Name | Default | Description                                      |
|:--- |:---- |:------- |:------------------------------------------------ |
| R   | inst |         | The instance to load the image into.             |
| R   | pix  |         | The image to load into Tesseract to perform OCR. |

**Details:**

Only 1 image can be set, calling this multiple times will replace the last image.

**Example:**

```jldoctest
julia> using Tesseract

julia> download_languages()
true

julia> instance = TessInst()
Allocated Tesseract instance.

julia> pix = sample_pix()
Image (500, 600) at 32ppi

julia> tess_image(instance, pix)
```

See also: [`tess_resolution`](@ref), [`pix_read`](@ref)
