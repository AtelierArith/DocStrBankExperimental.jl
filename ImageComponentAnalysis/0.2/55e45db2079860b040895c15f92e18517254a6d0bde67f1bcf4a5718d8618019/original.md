```
    BasicMeasurement <: AbstractComponentAnalysisAlgorithm
    BasicMeasurement(; area = true,  perimeter = true)
    analyze_components(components, f::BasicMeasurement)
    analyze_components!(dataframe::AbstractDataFrame, components, f::BasicMeasurement)
```

Takes as input an array of labelled connected components and returns a `DataFrame` with columns that store basic measurements, such as `area` and `perimeter`, of each component.

# Details

The `area` and `perimeter` measures are derived from *bit-quad* patterns, which are certain 2 × 2 pixel patterns described in [1]. Hence, the function adds six bit-quad patterns to the `DataFrame` under column names `Q₀, Q₁, Q₂, Q₃, Q₄` and `Qₓ`.

The function returns two measures for the `perimeter`, *perimiter₀* and *perimter₁*, which are given by equations 18.2-8b and 18.2-7a in [2]

# Example

```julia
using ImageComponentAnalysis, TestImages, ImageBinarization, ColorTypes

img = Gray.(testimage("blobs"))
img2 = binarize(img, Otsu())
components = label_components(img2, trues(3,3), 1)
measurements = analyze_components(components, BasicMeasurement(area = true, perimeter = false))

```

# References

1. S. B. Gray, “Local Properties of Binary Images in Two Dimensions,” IEEE Transactions on Computers, vol. C–20, no. 5, pp. 551–561, May 1971.
2. Pratt, William K., Digital Image Processing, New York, John Wiley & Sons, Inc., 1991, p. 629.
