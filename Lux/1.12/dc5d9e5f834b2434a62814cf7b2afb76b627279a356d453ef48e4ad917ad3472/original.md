```
PixelShuffle(r::Int)
```

Pixel shuffling layer with upscale factor `r`. Usually used for generating higher resolution images while upscaling them.

See `NNlib.pixel_shuffle` for more details.

## Arguments

  * `r`: Upscale factor

## Inputs

  * `x`: For 4D-arrays representing N images, the operation converts input `size(x) == (W, H, r² x C, N)` to output of size `(r x W, r x H, C, N)`. For D-dimensional data, it expects `ndims(x) == D + 2` with channel and batch dimensions, and divides the number of channels by `rᴰ`.

## Returns

  * Output of size `(r x W, r x H, C, N)` for 4D-arrays, and `(r x W, r x H, ..., C, N)` for D-dimensional data, where `D = ndims(x) - 2`
