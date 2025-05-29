```
    Matching <: AbstractHistogramAdjustmentAlgorithm
    Matching(targetimg; nbins = 256, edges = nothing)

    adjust_histogram([T,] img, f::Matching)
    adjust_histogram!([out,] img, f::Matching)
```

Returns a histogram matched image with a granularity of `nbins` number of bins. The first argument `img` is the image to be matched, whereas the argument `targetimg` in `Matching()` is the image having the desired histogram to be matched to.

# Details

The purpose of histogram matching is to transform the intensities in a source image so that the intensities distribute according to the histogram of a specified target image. If one interprets histograms as piecewise-constant models of probability density functions (see [`build_histogram`](@ref build_histogram(::AbstractArray, ::Integer, ::Union{Real,AbstractGray}, ::Union{Real,AbstractGray}))), then the histogram matching task can be modelled as the problem of transforming one probability distribution into another [1]. It turns out that the solution to this transformation problem involves the cumulative and inverse cumulative distribution functions of the source and target probability density functions.

In particular, let the random variables $x \thicksim p_{x}$ and $z \thicksim p_{z}$  represent an intensity in the source and target image respectively, and let

$$
 S(x) = \int_0^{x}p_{x}(w)\mathrm{d} w \quad \text{and} \quad
 T(z) = \int_0^{z}p_{z}(w)\mathrm{d} w
$$

represent their concomitant cumulative distribution functions. Then the sought-after mapping $Q(\cdot)$ such that $Q(x) \thicksim p_{z}$ is given by

$$
Q(x) =  T^{-1}\left( S(x) \right),
$$

where $T^{-1}(y) = \operatorname{min} \{ x \in \mathbb{R} : y \leq T(x) \}$ is the inverse cumulative distribution function of $T(x)$.

The mapping suggests that one can conceptualize histogram matching as performing histogram equalization on the source and target image and relating the two equalized histograms. Refer to [`adjust_histogram`](@ref adjust_histogram(::Equalization, ::AbstractArray, ::Integer, ::Union{Real,AbstractGray}, ::Union{Real,AbstractGray})) for more details on histogram equalization.

# Options

Various options for the parameters of the `adjust_histogram` function and `Matching` type are described in more detail below.

## Choices for `img` and `targetimg`

The `adjust_histogram(img, Matching())` function can handle a variety of input types. The type of the returned image matches the input type.

For colored images, the inputs are converted to [YIQ](https://en.wikipedia.org/wiki/YIQ)  type and the distributions of the Y channels are matched. The modified Y channel is then combined with the I and Q channels and the resulting image converted to the same type as the input.

## Choices for `nbins`

You can specify the total number of bins in the histogram. If you do not specify the number of bins then a default value of 256 bins is utilized.

## Choices for `edges`

If you do not designate the number of bins, then you have the option to directly stipulate how the intervals will be divided by specifying a `AbstractRange` type.

# Example

```julia
using Images, TestImages, ImageView

img_source = testimage("mandril_gray")
img_target = adjust_histogram(img_source, GammaCorrection(gamma = 0.5))
img_transformed = adjust_histogram(img_source, Matching(targetimg = img_target))
#=
    A visual inspection confirms that img_transformed resembles img_target
    much more closely than img_source.
=#
imshow(img_source)
imshow(img_target)
imshow(img_transformed)
```

# References

1. W. Burger and M. J. Burge. *Digital Image Processing*. Texts in Computer Science, 2016. [doi:10.1007/978-1-4471-6684-9](https://doi.org/10.1007/978-1-4471-6684-9)
