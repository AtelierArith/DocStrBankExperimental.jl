medfilt2 - Convenience wrapper for median filtering.

```
Usage:  medimg = medfilt2(img, h::Int, w::Int)
        medimg = medfilt2(img, h::Int)
        medimg = medfilt2(img, hw::Tuple)

Arguments:   img - Image to be processed, Array{T,2}
            h, w - Height and width of rectangular window over which the
                   median is to be computed. Values must be odd.
                   h and w may be specified as a size tuple, or as a
                   single value in which case w and h are made equal.

Returns:  medimg - Median filtered image.

```
