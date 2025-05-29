```
SingleHistogramThreshold <: AbstractImageBinarizationAlgorithm
SingleHistogramThreshold(alg::AbstractThresholdAlgorithm; nbins=256)

binarize([T,] img, f::AbstractThresholdAlgorithm; nbins=256)
binarize!([out,] img, f::AbstractThresholdAlgorithm; nbins=256)
```

Binarizes the image `img` using the threshold found by given threshold finding algorithm `alg`.

# Output

Return the binarized image as an `Array{Gray{T}}` of size `size(img)`. If `T` is not specified, it is inferred from `out` and `img`.

# Arguments

The function argument is described in more detail below.

## `img::AbstractArray`

The image that needs to be binarized.  The image is automatically converted to `Gray` in order to construct the requisite graylevel histogram.

## `alg::AbstractThresholdAlgorithm`

`AbstractThresholdAlgorithm` is an abstract type defined in `ThresholdAPI.jl` in the `HistogramThreshold.jl` package, it provides various threshold finding algorithms:

  * `HistogramThresholding.Balanced`
  * `HistogramThresholding.Entropy`
  * `HistogramThresholding.Intermodes`
  * `HistogramThresholding.MinimumError`
  * `HistogramThresholding.MinimumIntermodes`
  * `HistogramThresholding.Moments`
  * `HistogramThresholding.Otsu`
  * `HistogramThresholding.UnimodalRosin`
  * `HistogramThresholding.Yen`

For the more detailed explaination and the construction, please refer to each concrete algorithm. For example, type `?Otsu` in REPL will give you more details on how to use `Otsu` methods.

## `nbins::Integer`

The number of discrete bins that used to build the histogram. A smaller `nbins` could possibly gives a less noisy, or in other words, a smoother output. The default value is `256`.

# Examples

All the usage follows the same pattern, take `Otsu` as an example:

```julia
using TestImages, ImageBinarization

img = testimage("cameraman")
img_binary = binarize(img, Otsu())
```

It is less convenient, but still, you could also construct a `SingleHistogramThreshold` by yourself:

```julia
using TestImages, ImageBinarization

img = testimage("cameraman")
f = SingleHistogramThreshold(Otsu(), nbins=256)
img_binary = binarize(img, f)
```
