```
    BoundingBox <: AbstractComponentAnalysisAlgorithm
    BoundingBox(;  box_area = true)
    analyze_components(components, f::BoundingBox)
    analyze_components!(df::AbstractDataFrame, components, f::BoundingBox)
```

Takes as input an array of labelled connected components and returns a `DataFrame` with columns that store a tuple of `StepRange` types that demarcate the minimum (image axis-aligned) bounding box of each component.

The function can optionally also return the box area.

# Example

```julia
using ImageComponentAnalysis, TestImages, ImageBinarization, ColorTypes

img = Gray.(testimage("blobs"))
img2 = binarize(img, Otsu())
components = label_components(img2, trues(3,3), 1)
measurements = analyze_components(components, BoundingBox(box_area = true))

```
