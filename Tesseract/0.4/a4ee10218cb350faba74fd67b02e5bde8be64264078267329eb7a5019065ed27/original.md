```
tess_recognize(
    inst::TessInst
)::Bool
```

Perform the OCR extraction.  This will be called automatically if you call one of the retrieval functions so you don't need to call it directly.  Returns `false` if there was an error.

**Arguments:**

|   T | Name | Default | Description                                   |
| ---:|:---- |:------- |:--------------------------------------------- |
|   R | inst |         | The instance to perform the recognition with. |

**Example:**

```jldoctest
julia> using Tesseract

julia> download_languages("eng+fra")
true

julia> instance = TessInst("eng+fra")
Allocated Tesseract instance.

julia> pix = sample_pix()
Image (500, 600) at 32ppi

julia> tess_image(instance, pix)

julia> tess_resolution(instance, 72)

julia> tess_recognize(instance)
true
```

See also: [`tess_text`](@ref), [`tess_hocr`](@ref), [`tess_alto`](@ref), [`tess_tsv`](@ref), [`tess_parsed_tsv`](@ref).
