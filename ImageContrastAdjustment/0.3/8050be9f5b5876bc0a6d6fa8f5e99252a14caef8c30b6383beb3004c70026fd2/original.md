```
    LinearStretching <: AbstractHistogramAdjustmentAlgorithm
    LinearStretching(; [src_minval], [src_maxval],
                       dst_minval=0, dst_maxval=1,
                       no_clamp=false)

    LinearStretching((src_minval, src_maxval) => (dst_minval, dst_maxval))
    LinearStretching((src_minval, src_maxval) => nothing)
    LinearStretching(nothing => (dst_minval, dst_maxval))

    adjust_histogram([T,] img, f::LinearStretching)
    adjust_histogram!([out,] img, f::LinearStretching)
```

Returns an image where the range of the intensities spans the interval [`dst_minval`, `dst_maxval`].

# Details

Linear stretching (also called *normalization*) is a contrast enhancing transformation that is used to modify the dynamic range of the image. In particular, suppose that the input image has gray values in the range [A,B] and one wishes to change the dynamic range to [a,b] using a linear mapping, then the necessary transformation is given by the relation

$$
f(x) = (x-A) \frac{b-a}{B-A} + a.
$$

# Options

Various options for the parameters of the `adjust_histogram` and `LinearStretching` type  are described in more detail below.

## Choices for `img`

The function can handle a variety of input types. The returned image depends on the input type.

For colored images, the input is converted to the [YIQ](https://en.wikipedia.org/wiki/YIQ)  type and the intensities of the Y channel are stretched to the specified range. The modified Y channel is then combined with the I and Q channels and the resulting image converted to the same type as the input.

## Choices for `dst_minval` and `dst_maxval`

If destination value range `dst_minval` and `dst_maxval` are specified then intensities are mapped to the range [`dst_minval`, `dst_maxval`]. The default values are 0 and 1.

## Choices for `src_minval` and `src_maxval`

The source value range `src_minval` and `src_maxval` specifies the intensity range of input image. By default, the values are `extrema(img)` (finite). If custom values are provided, the output intensity value will be clamped to range `[dst_minval, dst_maxval]` if it exceeds that.

## `no_clamp`

Setting `no_clamp=true` to disable the automatic clamp even if the output intensity value exceeds the range `[dst_minval, dst_maxval]`. Note that a clamp is still applied for types that has limited value range, for example, if the input eltype is `N0f8`, then the output will be clamped to `[0.0N0f8, 1.0N0f8]` even if `no_clamp==true`.

# Example

```julia
using ImageContrastAdjustment, TestImages

img = testimage("mandril_gray")
# Stretches the contrast in `img` so that it spans the unit interval.
imgo = adjust_histogram(img, LinearStretching(dst_minval = 0, dst_maxval = 1))
```

For convenience, Constructing a `LinearStretching` object using `Pair` is also supported

```julia
# these two constructors are equivalent
LinearStretching(src_minval=0.1, src_maxval=0.9, dst_minval=0.05, dst_maxval=0.95)
LinearStretching((0.1, 0.9) => (0.05, 0.95))

# replace the part with `nothing` to use default values, e.g.,
# specify only destination value range
LinearStretching(nothing => (0.05, 0.95))
# specify only source value range and use default destination value range, i.e., (0, 1)
LinearStretching((0.1, 0.9) => nothing)
```

# References

1. W. Burger and M. J. Burge. *Digital Image Processing*. Texts in Computer Science, 2016. [doi:10.1007/978-1-4471-6684-9](https://doi.org/10.1007/978-1-4471-6684-9)
