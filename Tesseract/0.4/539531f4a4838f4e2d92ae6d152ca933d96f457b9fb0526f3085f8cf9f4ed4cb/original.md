```
tess_resolution(
    inst::TessInst, # The instance to configure.
    ppi             # The PPI of the source image.
)::Nothing
```

Set the resolution of the image in ppi.

**Arguments:**

| T   | Name | Default | Description                                    |
|:--- |:---- |:------- |:---------------------------------------------- |
| R   | inst |         | The instance of load the image into.           |
| R   | ppi  |         | The PPI (pixels per inch) of the source image. |

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

julia> tess_resolution(instance, 72)
```

See also: [`tess_image`](@ref)
