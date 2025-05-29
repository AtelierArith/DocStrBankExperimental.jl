```
    EllipseRegion <: AbstractComponentAnalysisAlgorithm
    EllipseRegion(;  centroid = true, semiaxes = true, orientation = true, eccentricity = true)
    analyze_components(components, f::EllipseRegion)
    analyze_components!(df::AbstractDataFrame, components, f::EllipseRegion)
```

Takes as input an array of labelled connected components and returns a `DataFrame` with columns that store the parameters of the best fit elliptic region for each component. The ellipse parameters are as follows:

1. `centroid`: A length-2 `SVector` representing the center of the ellipse.
2. `semiaxes`: A length-2 `SVector` representing the length of the semimajor and semiminor axes respectively.
3. `orientation` ∈ [-90, 90): the orientation in degrees of the semimajor axes with respect to the positive x-axis.
4. `eccentricity`: a measure of how nearly circular the ellipse is.

The ellipse region is estimated from [image moments](https://en.wikipedia.org/wiki/Image_moment) and hence the function adds moments to the `DataFrame` under column names `M₀₀, M₁₀, M₀₁, M₁₁, M₂₀` and `M₀₂`.

# Example

```julia
using ImageComponentAnalysis, TestImages, ImageBinarization, ImageCore, AbstractTrees

img = Gray.(testimage("blobs"))
img2 = binarize(img, Otsu())
components = label_components(img2, trues(3,3), 1)
measurements = analyze_components(components, EllipseRegion())

```

# Reference

1. [1] M. R. Teague, “Image analysis via the general theory of moments*,” Journal of the Optical Society of America, vol. 70, no. 8, p. 920, Aug. 1980.
