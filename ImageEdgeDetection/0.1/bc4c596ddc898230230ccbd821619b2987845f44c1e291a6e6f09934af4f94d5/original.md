```
    Canny <: AbstractEdgeDetectionAlgorithm
    Canny(; spatial_scale = 1, high = Percentile(80), low = Percentile(20), thinning_algorithm = NonmaximaSuppression(threshold = low))

    detect_edges([T,] img, f::Canny)
    detect_edges!([out,] img, f::Canny)
    detect_subpixel_edges([T₁, T₂] img, f::Canny)
    detect_subpixel_edges!(out₁, out₂, img, f::Canny)
```

Returns a binary image depicting the edges of the input image.

# Details

TODO

# Options

Various options for the parameters of the `detect_edges` function and `Canny` type are described in more detail below.

# Choices for img

The `detect_edges` function can handle a variety of input types. By default the type of the returned image matches the type of the input image.

For colored images, the input is converted to grayscale.

# Choices for `spatial_scale` in `Canny`.

The `spatial_scale` determines the radius (σ) of the Gaussian filter. It must be a positive real number.

# Choices for `high` and `low` in `Canny`.

The hysteresis thresholds `high` and `low` (`high` > `low`) can be specified as positive numbers, or as `Percentiles`. If left unspecified, a default value of `high = Percentile(80)` and `low = Percentile(20)` is assumed.

# Choices for `thinning_algorithm` in `Canny`.

You can specify an [`AbstractEdgeThinningAlgorithm`](@ref). By default, the [`NonmaximaSuppression`](@ref) algorithm is used which suppresses non-maxima up to pixel-level accuracy. For subpixel precision specify the [`SubpixelNonmaximaSuppression`](@ref) algorithm.

# Example

```julia

using TestImages, FileIO, ImageView

img =  testimage("mandril_gray")
img_edges = detect_edges(img, Canny(spatial_scale = 1.4))

imshow(img)
imshow(img_edges)
```

# References

J. Canny, "A Computational Approach to Edge Detection," in IEEE Transactions on Pattern Analysis and Machine Intelligence, vol. PAMI-8, no. 6, pp. 679-698, Nov. 1986, doi: 10.1109/TPAMI.1986.4767851.
