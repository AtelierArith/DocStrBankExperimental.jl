```
AdaptiveThreshold <: AbstractImageBinarizationAlgorithm
AdaptiveThreshold([img]; [window_size,] percentage = 15)

binarize([T,] img, f::AdaptiveThreshold)
binarize!([out,] img, f::AdaptiveThreshold)
```

Binarize `img` using a threshold that varies according to background illumination.

# Output

Return the binarized image as an `Array{Gray{T}}` of size `size(img)`. If `T` is not specified, it is inferred from `out` and `img`.

# Extended help

# Details

If the value of a pixel is `t` percent less than the average of an $s \times s$ window of pixels centered around the pixel, then the pixel is set to black, otherwise it is set to white.

A computationally efficient method for computing the average of an $s \times s$ neighbourhood is achieved by using an *integral image* `integral_image`.

This algorithm works particularly well on images that have distinct contrast between background and foreground. See [1] for more details.

# Arguments

The function argument is described in more detail below.

## `img::AbstractArray`

The image that need to be binarized. The image is automatically converted to `Gray` in order to construct the requisite graylevel histogram.

You can also pass `img` to `AdaptiveThreshold` to automatically infer the "best" `window_size`.

# Options

Various options for the parameters of `AdaptiveThreshold`, `binarize` and `binarize!` are described in more detail below.

## Choices for `percentage`

You can specify an integer for the `percentage` (denoted by `t` in [1]) which must be between 0 and 100. Default: 15

## Choices for `window_size`

The argument `window_size` (denoted by `s` in [1]) specifies the size of pixel's square neighbourhood which must be greater than zero.

If `img` is passed to `AdaptiveThreshold` constructor, then `window_size` is infered as the integer closest to 1/8 of the average of the width and height of `img`.

# Examples

```julia
using TestImages

img = testimage("cameraman")
f = AdaptiveThreshold(window_size = 16)
img₀₁ = binarize(img, f)

f = AdaptiveThreshold(img) # infer the best `window_size` using `img`
img₀₁ = binarize(img, f)
```

See also [`binarize!`](@ref) for in-place operation.

# References

[1] Bradley, D. (2007). Adaptive Thresholding using Integral Image. *Journal of Graphic Tools*, 12(2), pp.13-21. [doi:10.1080/2151237x.2007.10129236](https://doi.org/10.1080/2151237x.2007.10129236)
