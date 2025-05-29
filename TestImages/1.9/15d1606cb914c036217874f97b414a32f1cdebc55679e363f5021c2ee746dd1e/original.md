```
img = testimage(filename; download_only=false, [ops...]
```

Load image from the DIP3E textbook that partially matches `filename` in case-insensitive manner.

If `download_only=true`, the full filepath is returned. Any other keyword `ops` will be passed to image IO backend through `FileIO.load`.

# Example

```julia
julia> using TestImages
julia> img = testimage_dip3e("cameraman") # matches Fig0222(b)(cameraman).tif
julia> img = testimage_dip3e("fig0222(a)")
```

!!! note "License"
    Permission is required from the owner of a © image if the image is used for other than personal educational or research purposes. See copyright file: https://www.imageprocessingplace.com/DIP-3E/dip3e_copyrights.htm.


DIP3E: "Digital Image Processing, 3rd edition" by Rafael C. Gonzalez and Richard E. Woods
