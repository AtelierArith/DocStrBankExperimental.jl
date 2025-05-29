```
    MinimumOrientedBoundingBox <: AbstractComponentAnalysisAlgorithm
    MinimumOrientedBoundingBox(;  oriented_box_area = true, oriented_box_aspect_ratio = true)
    analyze_components(components, f::MinimumOrientedBoundingBox)
    analyze_components!(df::AbstractDataFrame, components, f::MinimumOrientedBoundingBox)
```

Takes as input an array of labelled connected components and returns a `DataFrame` with columns that store a length-4 vector containing the four corner points of the minimum oriented bounding box of each component. It optionally also returns the area and aspect ratio of the minimum oriented bounding box.

# Example

```julia
using ImageComponentAnalysis, TestImages, ImageBinarization, ColorTypes

img = Gray.(testimage("blobs"))
img2 = binarize(img, Otsu())
components = label_components(img2, trues(3,3), 1)
algorithm = MinimumOrientedBoundingBox(oriented_box_area = true, oriented_box_aspect_ratio = true)
measurements = analyze_components(components, algorithm)

```
