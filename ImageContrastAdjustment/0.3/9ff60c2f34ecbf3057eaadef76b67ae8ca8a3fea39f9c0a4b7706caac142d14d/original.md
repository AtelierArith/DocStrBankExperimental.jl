```
    ContrastStretching <: AbstractHistogramAdjustmentAlgorithm
    ContrastStretching(; t = 0.5,  slope = 1.0)

    adjust_histogram([T,] img, f::ContrastStretching)
    adjust_histogram!([out,] img, f::ContrastStretching)
```

Returns an image where intensities below `t` are compressed into a narrower range of dark intensities, and values above `t` are compressed into a narrower band of light intensities.

# Details

Contrast stretching is a transformation that  enhances or reduces (for `slope` > 1 or < 1, respectively) the contrast near saturation (0 and 1). It is given by the relation

$$
f(x) = \frac{1}{1 + \left(\frac{t}{x} \right)^s}, \; s \in \mathbb{R},
$$

where $s$ represents the `slope` argument.

# Options

Various options for the parameters of the `adjust_histogram` and `ContrastStretching` type are described in more detail below.

## Choices for `img`

The function can handle a variety of input types. The returned image depends on the input type.

For colored images, the input is converted to the [YIQ](https://en.wikipedia.org/wiki/YIQ)  type and the intensities of the Y channel are stretched to the specified range. The modified Y channel is then combined with the I and Q channels and the resulting image converted to the same type as the input.

## Choice for `t`

The value of `t` needs to be in the unit interval. If left unspecified a default value of 0.5 is utilized.

## Choice for `slope`

The value of `slope` can be any real number. If left unspecified a default value of 1.0 is utilized.

# Example

```julia
using ImageContrastAdjustment, ImageView, TestImages

img = testimage("mandril_gray")
ret = adjust_histogram(img, ContrastStretching(t = 0.6, slope = 3))

```

# References

1. Gonzalez, R. C., Woods, R. E., & Eddins, S. L. (2004). *Digital image processing using MATLAB* (Vol. 624). Upper Saddle River, New Jersey: Pearson-Prentice-Hall.
