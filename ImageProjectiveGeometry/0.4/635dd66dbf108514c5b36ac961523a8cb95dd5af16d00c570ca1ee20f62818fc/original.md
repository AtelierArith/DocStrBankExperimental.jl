stdfilt2 - Compute local standard deviation across an image.

```
Usage:  stdimg = stdfilt2(img, h::Int, w::Int)
        stdimg = stdfilt2(img, h::Int)
        stdimg = stdfilt2(img, hw::Tuple)

Arguments:   img - Image to be processed, Array{T,2}
            h, w - Height and width of rectangular window over which the
                   standard deviation is to be computed. Values must be odd.
                   h and w may be specified as a size tuple, or as a
                   single value in which case w and h are made equal.

Returns:  stdimg - Standard deviation image.

```
