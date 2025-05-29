```
tess_confidences(
    inst::TessInst
)::Union{Vector{Int}, Nothing}
```

Extract the confidences in the words that where extracted from the image.

**Arguments:**

| T   | Name | Default | Description                     |
|:--- |:---- |:------- |:------------------------------- |
| R   | inst |         | The Tesseract instance to call. |

**Details:**

This method will call `tess_recognize()` if it has not been called yet for the image.

**Example:**

```jldoctest
using Tesseract

download_languages()

instance = TessInst()
pix = sample_pix()

tess_image(instance, pix)
tess_resolution(instance, 72)

confidence = tess_confidences(instance)

# output

256-element Vector{Int64}:
 95
 95
 92
 92
 96
 96
 96
 96
 96
 96
  ⋮
 96
 96
 96
 96
 96
 96
 96
 86
 86
```

See also: [`tess_tsv`](@ref), [`tess_parsed_tsv`](@ref)
