```
sample_pix()::Pix
```

Generate a sample image with text.

**Details:**

The primary purpose of this method is to make it easier to demonstrate the functionality of the Tesseract library by providing a Pix object for an image with text that can be processed by Tesseract.

The text on this image is the first paragraph of the book War of World by H.G. Wells. This book is in the public domain, so no copyright exists.

**Example:**

```jldoctest
julia> using Tesseract

julia> update_languages()
true

julia> instance = TessInst()
Allocated Tesseract instance.

julia> pix = sample_pix()
Image (500, 600) at 32ppi

julia> tess_image(instance, pix)

julia> tess_resolution(instance, 72)

julia> text = tess_text(instance);
```

See also: [`sample_tiff`](@ref)
