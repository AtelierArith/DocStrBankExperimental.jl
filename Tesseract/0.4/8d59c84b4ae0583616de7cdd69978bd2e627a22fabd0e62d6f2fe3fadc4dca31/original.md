```
tess_text(
    inst::TessInst
)::Union{String, Nothing}
```

Extract the text from the image. If there is an error `nothing` will be returned.

**Arguments:**

| T   | Name | Default | Description                         |
|:--- |:---- |:------- |:----------------------------------- |
| R   | inst |         | The instance to grab the text from. |

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

text = tess_text(instance)

for line in split(text, '\n'; keepempty = false)[1:5]
    println(line)
end

# output

No one would have believed in the last years of the
the nineteenth century that this world was being watched
watched keenly and closely by intelligences greater than
than man’s and yet as mortal as his own; that as men busied
busied themselves about their various concerns they were
```

See also: [`tess_hocr`](@ref), [`tess_alto`](@ref), [`tess_tsv`](@ref),           [`tess_parsed_tsv`](@ref), [`tess_confidences`](@ref)
