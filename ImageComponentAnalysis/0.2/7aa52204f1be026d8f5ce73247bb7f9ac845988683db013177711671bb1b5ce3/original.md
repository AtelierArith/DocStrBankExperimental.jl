```
    BasicTopology <: AbstractComponentAnalysisAlgorithm
    BasicTopology(; holes = true,  euler_number = true)
    analyze_components(components, f::BasicTopolgy)
    analyze_components!(dataframe::AbstractDataFrame, components, f::BasicTopolgy)
```

Takes as input an array of labelled connected components and returns a `DataFrame` with columns that store basic topological properties for each component, such as the `euler_number` and the total number of `holes`.

The function returns two variants of the `euler_number`: `euler₄` and `euler₈` which correspond to a `4-connected` versus `8-connected` neighbourhood.

The `euler_number` and number of `holes` are derived from *bit-quad* patterns, which are certain 2 × 2 pixel patterns described in [1]. Hence, the function adds six bit-quad patterns to the `DataFrame` under column names `Q₀, Q₁, Q₂, Q₃, Q₄` and `Qₓ`.

# Example

```julia
using ImageComponentAnalysis, TestImages, ImageBinarization, ColorTypes

img = Gray.(testimage("blobs"))
img2 = binarize(img, Otsu())
components = label_components(img2, trues(3,3), 1)
measurements = analyze_components(components, BasicTopology(holes = true, euler_number = true))

```

# Reference

1. S. B. Gray, “Local Properties of Binary Images in Two Dimensions,” IEEE Transactions on Computers, vol. C–20, no. 5, pp. 551–561, May 1971.
