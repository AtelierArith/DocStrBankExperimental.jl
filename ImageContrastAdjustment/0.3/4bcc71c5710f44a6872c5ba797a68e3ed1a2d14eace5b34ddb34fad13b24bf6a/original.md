```
    MidwayEqualization <: AbstractHistogramAdjustmentAlgorithm
    MidwayEqualization(; nbins = 256, minval = 0, maxval = 1)

    adjust_histogram([T,] img_sequence, f::MidwayEqualization(nbins = 256, edges = nothing))
    adjust_histogram!([out_sequence,] img_sequence, f::MidwayEqualization(nbins = 256, edges = nothing))
```

Gives a pair of images the same histogram whilst maintaining as much as possible their previous grey level dynamics.

# Details

The purpose of midway histogram equalization is to transform the intensities in a pair of images so that the intensities distribute according to a common "midway" distribution. The histogram representing the common distribution is chosen so that the original  gray level dynamics of the images are preserved as much as possible. If one interprets histograms as piecewise-constant models of probability density functions (see [`build_histogram`](@ref build_histogram(::AbstractArray, ::Integer, ::Union{Real,AbstractGray}, ::Union{Real,AbstractGray}))), then the midway histogram equalization task can be modeled as the problem of transforming one probability distribution into another (see [`adjust_histogram`](@ref adjust_histogram(::Matching,::AbstractArray, ::AbstractArray, ::Integer))). It turns out that the solution to this transformation problem involves the cumulative and inverse cumulative distribution functions of the source and "midway" probability density functions. In particular, let the random variables $X_i \thicksim p_{x_i} \; (i = 1,2)$, and $Z \thicksim p_{z}$  represent an intensity in the first, second and "midway" image respectively, and let

$$
 S_{X_i}(x) = \int_0^{x}p_{x_i}(w)\mathrm{d} w \; \quad \text{and} \quad
 T_{Z}(x) = \frac{2}{\frac{1}{S_{X_1}(x)} + \frac{1}{S_{X_2}(x)}}
$$

represent the cumulative distribution functions of the two input images, and their *harmonic mean*, respectively. Then the sought-after mapping $Q_{X_i}(\cdot)$ $(i = 1,2)$ such that $Q_{X_i}(x) \thicksim p_{z}$ is given by

$$
Q_{X_i}(x) =  T_{Z}^{-1}\left( S_{X_i}(x) \right),
$$

where $T_{Z}^{-1}(y) = \operatorname{min} \{ x \in \mathbb{R} : y \leq T_{Z}(x) \}$ is the inverse cumulative distribution function of $T_{Z}(x)$.

# Options

Various options for the parameters of the `adjust_histogram` function and `MidwayEqualization` types are described in more detail below.

## Choices for `img_sequence`

The function `adjust_histogram` expects a length-2 `Vector` of images (the pair of images) and returns a length-2 `Vector` of modified images.  The  function can handle a variety of input types. The type of the returned image matches the input type.

For colored images, the inputs are converted to [YIQ](https://en.wikipedia.org/wiki/YIQ)  type and the distributions of the Y channels are transformed according to a "midway" distribution. The modified Y channel is then combined with the I and Q channels and the resulting image converted to the same type as the input.

## Choices for `nbins`

You can specify the total number of bins in the histogram. If you do not specify the number of bins then a default value of 256 bins is utilized.

## Choices for `edges`

If you do not designate the number of bins, then you have the option to directly stipulate how the intervals will be divided by specifying a `AbstractRange` type.

# Example

```julia
using Images, TestImages, ImageView, ImageContrastAdjustment

img = testimage("mandril_gray")

# The same image but with different intensitiy distributions
img1 = adjust_histogram(img, GammaCorrection(gamma = 2))
img2 = adjust_histogram(img, GammaCorrection(gamma = 1.2))

# Midway histogram equalization will transform these two images so that their
# intensity distributions are almost identical.
img_sequence = adjust_histogram([img1, img2], MidwayEqualization(nbins = 256))
img1o = first(img_sequence)
img2o = last(img_sequence)
```

# References

1. T. Guillemot and J. Delon, “*Implementation of the Midway Image Equalization*,” Image Processing On Line, vol. 5, pp. 114–129, Jun. 2016. [doi:10.5201/ipol.2016.140](https://doi.org/10.5201/ipol.2016.140)
