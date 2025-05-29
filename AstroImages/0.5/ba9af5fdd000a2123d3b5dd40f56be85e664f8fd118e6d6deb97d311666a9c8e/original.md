```
img1, img2 = AstroImage(filename::AbstractString, exts)
```

Load multiple image HDUs `exts` from an FITS file at `filename` as an AstroImage. `exts` must be a tuple, range, :, or array of Integers. All listed HDUs in `exts` must be image HDUs or an error will occur.

Example:

```julia
img1, img2 = AstroImage("abc.fits", (1,3)) # loads the first and third HDU as images.
imgs = AstroImage("abc.fits", 1:3) # loads the first three HDUs as images.
imgs = AstroImage("abc.fits", :) # loads all HDUs as images.
```
