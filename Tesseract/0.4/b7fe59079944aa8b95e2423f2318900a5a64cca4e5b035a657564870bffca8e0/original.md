```
sample_tiff()::Vector{UInt8}
```

Generate a byte array containing a TIFF image with text.

**Details:**

The primary purpose of this method is to make it easier to demonstrate the functionality of the Tesseract library by providing a byte stream of an image with text that can be processed by Tesseract.

The text on this image is the first paragraph of the book War of World by H.G. Wells. This book is in the public domain, so no copyright exists.

**Example:**

```jldoctest
julia> using Tesseract

julia> data = sample_tiff();

julia> pix = pix_read_tiff(data)
Image (500, 600) at 32ppi
```

See also: [`sample_pix`](@ref)
